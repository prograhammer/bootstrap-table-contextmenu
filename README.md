Bootstrap table context menu
=======================

This is a light-weight extension for wenzhixin's [Bootstrap table](http://bootstrap-table.wenzhixin.net.cn/) that adds context menu support. 

Features
-----
- Supports both right-clicking a row or clicking on a button on the row to bring up a context menu.
- Works elegantly with Bootstrap dropdown menus and Font-Awesome.
- Events for menu and item clicks.

Demo
-----
See various features in action: [demo here](http://www.prograhammer.com/demos/bootstrap-table-contextmenu)

Usage
-----
### Simple example
First of all, you need to include Bootstrap and this extension:
```
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css">

<script src="https://code.jquery.com/jquery-2.1.4.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js"></script>
<script src="../src/bootstrap-table-contextmenu.js"></script>
```

Then you can create your dropdown menu element and use its selector in the table settings javascript:
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
      $('#grid').bootstrapTable({
          contextMenu: '#context-menu',
          onContextMenuItem: function(row, $el){
              if($el.data("item") == "edit"){
                  alert(row.itemid);
              }
          }
      });
    </script>
</body>
```
