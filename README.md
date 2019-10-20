# SeatBooking_RecyclerView
RecyclerView with SeatBooking layout


<a href="https://github.com/naveendew/SeatBookRecyclerView/blob/new/device-2018-02-21-114946.png"><img src="https://github.com/naveendew/SeatBookRecyclerView/blob/new/device-2018-02-21-114946.png" height="403" width="240" />
</a>
<a href="https://github.com/naveendew/SeatBookRecyclerView/blob/new/device-2018-02-21-120217.png"><img src="https://github.com/naveendew/SeatBookRecyclerView/blob/new/device-2018-02-21-120217.png" height="403" width="240" /></a>

<a href="https://github.com/naveendew/SeatBookRecyclerView/blob/new/device-2018-02-21-120853.png"><img src="https://github.com/naveendew/SeatBookRecyclerView/blob/new/device-2018-02-21-120853.png" height="403" width="240" /></a>


<h2>Credit</h2>
https://github.com/TakeoffAndroid/SeatBookingRecyclerView















In this post, i am going to implement a RecyclerView with multi and single selection feature. In multi selection, user can select multiple items from recycler view and in single selection, user can select only one item from the recycler view.
Now lets start..
Suppose there is a model class called Item which holds name and surname. We override equals method in this class in order to compare Item instances.

We start with decorating it with selectable feature, so that it has a selection state:

Next is the view holder:

We hold an instance of SelectableItem in view holder. On check event of the CheckedTextView, we update the selection state of the SelectableItem. If the recycler view is a multi selection list, we allow deselection. We also update the appearance of the CheckedTextView as selected by changing background color. Finally, we call the onItemSelected of the listener which is adapter in our case.
Now lets see the adapter:

SelectableAdapter’s constructor gets the list type as parameter: multi or single selection, adapter data and a listener which is the activity. Listener will be called when there is a click on an item in the list. getItemViewType returns the list type. Behaviour of the list changes depending on this. At onBindViewHolder, we draw a rectangle checkbox if multi selection is enabled, or a radiobutton if not enabled. You may need the selected items, so there is getSelectedItems method.
When multi selection is enabled, you can check/uncheck items as intented, this is default behaviour. But when multi selection is disabled, we need to deselect other check boxes. So in onItemSelected method, we loop over items and select the clicked check box and deselect others. Remember that onItemSelected is called in ViewHolder when there is a click.
Next is the activity:

We initialize the recycler view in onCreate and activity also implements onItemSelectedListener interface, in case you need the activity get notified when an item is clicked.
Below is the views used in this sample:


This completes my post. Hope this post helps you.
