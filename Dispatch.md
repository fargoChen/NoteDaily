# Android 6.0 Marshmallow Failed to dispatch

logs as Warn like:
W/WindowAnimator: Failed to dispatch window animation state change.
W/WindowAnimator: android.os.DeadObjectException

solution:
find the view with animation and set:
View.setLayerType(View.LAYER_TYPE_SOFTWARE);
