Callback and Handlers
======================

✅ 1. Button Callbacks

ElevatedButton, TextButton, IconButton, FloatingActionButton

	•	onPressed

	•	onLongPress

	•	onHover

	•	onFocusChange

⸻

✅ 2. Gesture Callbacks (GestureDetector / InkWell / InkResponse)

Tap gestures

	•	onTap

	•	onTapDown

	•	onTapUp

	•	onTapCancel

Double-tap

	•	onDoubleTap

Long press

	•	onLongPress

	•	onLongPressStart

	•	onLongPressMoveUpdate

	•	onLongPressEnd

	•	onLongPressUp

Pan / Drag

	•	onPanStart

	•	onPanUpdate

	•	onPanEnd

	•	onHorizontalDragStart

	•	onHorizontalDragUpdate

	•	onHorizontalDragEnd

	•	onVerticalDragStart

	•	onVerticalDragUpdate

	•	onVerticalDragEnd

Force press

	•	onForcePressStart

	•	onForcePressPeak

	•	onForcePressEnd

Scale / Pinch

	•	onScaleStart

	•	onScaleUpdate

	•	onScaleEnd

Other gestures

	•	onSecondaryTap

	•	onSecondaryTapUp

	•	onSecondaryTapDown

	•	onTertiaryTapDown

	•	onTertiaryTapUp

⸻

✅ 3. TextField / TextFormField Callbacks

	•	onChanged

	•	onEditingComplete

	•	onSubmitted

	•	onTap

	•	onTapOutside

	•	onSaved ⚠️ (in forms)

	•	validator (returns String?)

	•	onFieldSubmitted

⸻

✅ 4. Checkbox / Switch / Radio Callbacks

	•	onChanged

Checkbox:
	•	onChanged

Switch:
	•	onChanged

Radio:
	•	onChanged

⸻

✅ 5. Slider Callbacks

	•	onChanged

	•	onChangeStart

	•	onChangeEnd

⸻

✅ 6. Scroll Callbacks

ListView, ScrollController

	•	onNotification (using NotificationListener)

	•	ScrollController listeners via:

	•	addListener()

⸻

✅ 7. Form Callbacks

	•	onWillPop (using WillPopScope)

	•	onSaved

	•	validator

	•	onChanged (FormField)

⸻

✅ 8. Page and Navigation Callbacks

PageView
	•	onPageChanged

Navigator

You register callbacks (not properties) by:

	•	.then() when popping a route

	•	using RouteObserver for:

	•	didPush

	•	didPop

	•	didReplace

	•	didRemove

⸻

✅ 9. Animation Callbacks

AnimationController

	•	addListener

	•	addStatusListener

Status options:

	•	AnimationStatus.forward

	•	AnimationStatus.reverse

	•	AnimationStatus.completed

	•	AnimationStatus.dismissed

⸻

✅ 10. Lifecycle Callbacks

StatefulWidget lifecycle

	•	initState

	•	didChangeDependencies

	•	didUpdateWidget

	•	setState (handler to update UI)

	•	dispose

	•	build

⸻

✅ 11. Focus & Keyboard Callbacks

FocusNode
	•	addListener

Shortcuts/Actions (like your app)
	•	onInvoke

⸻

✅ 12. App Lifecycle Callbacks

Using WidgetsBindingObserver

	•	didChangeAppLifecycleState

	•	resumed

	•	inactive

	•	paused

	•	detached

⸻

✅ 13. Miscellaneous Widget Callbacks

Switches, Toggles, Pickers:

	•	onDateChanged

	•	onTimeChanged

	•	onSelectedItemChanged (CupertinoPicker)

Drawer:

	•	onDrawerOpened

	•	onDrawerClosed

ExpansionTile:
	•	onExpansionChanged

RefreshIndicator:
	•	onRefresh

⸻

⭐ SUMMARY

Here is the clean shortest summary:

Most common callbacks in Flutter:

	•	onPressed

	•	onTap

	•	onChanged

	•	onSubmitted

	•	onLongPress

	•	onHover

	•	onSaved

	•	validator

	•	onPageChanged

	•	addListener (for controllers)

	•	onWillPop

	•	onRefresh

	•	onInvoke

Most common handlers:

	•	Tap handler → onTap

	•	Press handler → onPressed

	•	Change handler → onChanged

	•	Drag handler → onPanUpdate, etc.

	•	Keyboard handler → onSubmitted

	•	Scroll handler → ScrollController listener

	•	Animation handler → AnimationController listeners
    