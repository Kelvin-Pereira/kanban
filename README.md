Here's an **overview of the default values**.
```js
var kanban = new jKanban({
    element          : '',                                           // selector of the kanban container
    gutter           : '15px',                                       // gutter of the board
    widthBoard       : '250px',                                      // width of the board
    responsivePercentage: false,                                    // if it is true I use percentage in the width of the boards and it is not necessary gutter and widthBoard
    dragItems        : true,                                         // if false, all items are not draggable
    boards           : [],                                           // json of boards
    dragBoards       : true,                                         // the boards are draggable, if false only item can be dragged
    addItemButton    : false,                                        // add a button to board for easy item creation
    buttonContent    : '+',                                          // text or html content of the board button
    itemHandleOptions: {
        enabled             : false,                                 // if board item handle is enabled or not
        handleClass         : "item_handle",                         // css class for your custom item handle
        customCssHandler    : "drag_handler",                        // when customHandler is undefined, jKanban will use this property to set main handler class
        customCssIconHandler: "drag_handler_icon",                   // when customHandler is undefined, jKanban will use this property to set main icon handler class. If you want, you can use font icon libraries here
        customHandler       : "<span class='item_handle'>+</span> %s"// your entirely customized handler. Use %s to position item title
    },
    click            : function (el) {},                             // callback when any board's item are clicked
    dragEl           : function (el, source) {},                     // callback when any board's item are dragged
    dragendEl        : function (el) {},                             // callback when any board's item stop drag
    dropEl           : function (el, target, source, sibling) {},    // callback when any board's item drop in a board
    dragBoard        : function (el, source) {},                     // callback when any board stop drag
    dragendBoard     : function (el) {},                             // callback when any board stop drag
    buttonClick      : function(el, boardId) {}                      // callback when the board's button is clicked
})
```

Now take a look to the `boards` object
```js
[
    {
        "id"    : "board-id-1",               // id of the board
        "title" : "Board Title",              // title of the board
        "class" : "class1,class2,...",        // css classes to add at the title
        "dragTo": ['another-board-id',...],   // array of ids of boards where items can be dropped (default: [])
        "item"  : [                           // item of this board
            {
                "id"    : "item-id-1",        // id of the item
                "title" : "Item 1"            // title of the item
                "class" : ["myClass",...]     // array of additional classes
            },
            {
                "id"    : "item-id-2",
                "title" : "Item 2"
            }
        ]
    },
    {
        "id"    : "board-id-2",
        "title" : "Board Title 2"
    }
]
```
 **WARNING: all ids are unique!**

### About custom properties
jKanban also support custom properties on items to improve your applications with html data- properties. You can define them at like:
```js
[
    {
        "id"    : "board-id-1",
        "title" : "Board Title",
        "item"  : [
            {
                "id"      : "item-id-1",
                "title"   : "Item 1",
                "username": "username1"
            },
            {
                "id"      : "item-id-2",
                "title"   : "Item 2",
                "username": "username2"
            }
        ]
    }
]


Method Name           | Arguments                        | Description
----------------------|----------------------------------|------------------------------------------------------------------------------------------------------------------------------
`addElement`          | `boardID, element`               | Add `element` in the board with ID `boardID`, `element` is the standard format
`addForm`             | `boardID, formItem`              | Add `formItem` as html element into the board with ID `boardID`
`addBoards`           | `boards`                         | Add one or more boards in the kanban, `boards` are in the standard format
`findElement`         | `id`                             | Find board's item by `id`
`replaceElement`      | `id, element`                    | Replace item by `id` with `element` JSON standard format
`getParentBoardID`    | `id`                             | Get board ID of item `id` passed
`findBoard`           | `id`                             | Find board by `id`
`getBoardElements`    | `id`                             | Get all item of a board
`removeElement`       | `id`                             | Remove a board's element by id
`removeBoard`         | `id`                             | Remove a board by id

//__buildItemTitle function para criação do card

 // add quanticades de card

 // 'kanban-board-header' add essa class para mover os blocos
 // result = "<div class='item_handle "+customCssHandler+"'><i class='item_handle "+customCssIconHandler+"'></i></div><div class='item_handle'>" + result + "</div>";


 //Status
 //Processando ( Atribuido )
 //Processando ( Pendende )
 //Pendende
 //Solucionado