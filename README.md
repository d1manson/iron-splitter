iron-splitter
=============

Based on core-splitter, ported to Polymer 1.0 by Juan Carlos Orozco (Feb. 2016), and then further tweaked by d1manson.

`iron-splitter` provides a split bar and dragging on the split bar
will resize the sibling element.  Use its `direction` property to indicate
which sibling element to be resized and the orientation.  `direction` can
be one of `up`, `down`, `left`, `right`.

Example showing a horizontal panel of three sections, divided by two splitters:

```html
<div style="display:flex;flex-direction:row">
  
  <iron-resize-notifier style="flex:0 0 0%;">
	section 1
  </iron-resize-notifier>
  
  <iron-splitter direction="left"></iron-splitter>
  
  <iron-resize-notifier style="flex:1 1 0%;">
	section 2
  </iron-resize-notifier>

  <iron-splitter direction="right"></iron-splitter>

  <iron-resize-notifier style="flex:0 0 0%;">
	section 1
  </iron-resize-notifier>
  
</div>
```

For vertical splitting use `flex-direction:column` in the parent, and `up`/`down` for the splitters.
If you want more than two sections...good luck!!  If you don't use flex values as shown here expect
bad results.

The `iron-resize-notifier` is basically a `div` with `IronResizableBehavior`.  That means
it will forward iron-resize events to its children, which is useful in the context
of the splitter because resizing can happen.  You can use a basic `div` or other element
if you don't have any code within the given section that wants to be informed of `'iron-resize'`
events.  And of course note that you need `IronReisableBehavior` at every level of the 
hierarchy between the splitter and your node of interest, otherwise the event won't get
forwarded all the way down.

The other properties for `iron-splitter` are:
*  `locked` - set to `true` to disable dragging.
*  `minSize` - empty string or value in `px`. Target element will not shrink below this
   width/height....currently not implemented.


