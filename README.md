Bootstrap table context menu
=======================

This is a super light-weight extension for wenzhixin's [Bootstrap table](http://bootstrap-table.wenzhixin.net.cn/) that adds context menu support. 

Features
-----
- Supports both right-clicking a row or clicking on a button on the row to bring up a context menu.
- Works elegantly with Bootstrap dropdown menus and Font-Awesome.
- Events for menu and item clicks.

Demo
-----
See it in action: [demo here](http://www.prograhammer.com/demos/bootstrap-table-contextmenu)

Installation
-----
###Bower
```
bower install bootstrap-table-contextmenu
```

Usage
-----
Include this extension after [Bootstrap-table](https://github.com/wenzhixin/bootstrap-table):
```
<script src="bootstrap-table-contextmenu.js"></script>
```

Simple example:
```
<body>
    <div class="container">
      <div class="row">
        <table id='grid'>
            <thead>
              <tr>
                <th data-field='itemid'>Item ID</th>
                <th data-field='name'>Name</th>
                <th data-field='price'>Price</th>
              </tr>
            </thead>
            <tbody>
              <tr><td>1</td><td>ABC</td><td>$1.00</td></tr>
              <tr><td>2</td><td>DEF</td><td>$2.00</td></tr>
              <tr><td>3</td><td>GHI</td><td>$3.00</td></tr>
              <tr><td>4</td><td>XYZ</td><td>$4.00</td></tr>
            </tbody>
        </table>
      </div>  
    </div>
  
    <!-- context menu -->
    <ul id="context-menu" class="dropdown-menu">
        <li data-item="edit"><a>Edit</a></li>
        <li data-item="delete"><a>Delete</a></li>
        <li data-item="action1"><a>Action Here</a></li>
        <li data-item="action2"><a>And Action Here</a></li>
    </ul>  

    <script>
	  $(function() {
		  $('#grid').bootstrapTable({
			  contextMenu: '#context-menu',
			  onContextMenuItem: function(row, $el){
				  if($el.data("item") == "edit"){
					  alert(row.itemid);
				  }
			  }
		  });
	  });
    </script>
</body>
```

Table Options
-----

|Name                    |Type                 |Default   |Description|
|------------------------|---------------------|----------|-----------|
|contextMenu             |String               |undefined |A jQuery selector that indicates the contextmenu.            |
|contextMenuButton       |String               |undefined |A jQuery selector for a button on each table row to use to trigger open the contextmenu (good for touch screens).       |
|contextMenuTrigger      |'right','left','both'|'right'   |Set what type of click will open the context menu.           |
|contextMenuAutoClickRow |Boolean              |false     |When the context menu is opened, also perform a left click on the row to select it.|

Events
-----

|Option Event           |jQuery Event               |Parameter     |Description|
|-----------------------|---------------------------|--------------|-----------|
|onContextMenuItem      |contextmenu-item.bs.table  |row, $element |This is all you will typically need. Fires when you click on a <code>li</code> on the contextmenu. | 
|onContextMenuRow       |contextmenu-row.bs.table   |row, $element |Fires when you right-click on a row. |
