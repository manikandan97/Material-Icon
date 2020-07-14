# Material-Icon

Material System Icons is a set of mobile platform icons.

## Icon List

[View the full list of icons](icons.md)

## Installation
### Android
The library is published via JCenter, please ensure that the `jcenter()` repository has been added to the root `build.gradle` file:
```groovy
repositories {
			...
			maven { url 'https://jitpack.io' }
		}
```
Include the following dependency in your project's `build.gradle`
```groovy
implementation 'com.github.manikandan97:Material-Icon:0.1.0'
```

# Documentation

## Usage
The library offers icons in the form of Android `VectorDrawable`, the icon names are structured as: 
> `R.drawable.ic_fluent_[name]_[size]_[style]`

* `name` - Name of the icon from [assets](../assets) that is all lowercased and underscore separated.
* `size` - Size of the icon that is one of 16/20/24/28/48. Note that some icons do not have all sizes available yet. Our designers are working to add missing ones to complete the collection.
* `style` - Style of the icon that is one of `regular`, `filled` or `selector`. See the section below for details.


## Tinting
With Android 5.0 (API level 21) and above, you can tint drawables with color resources or theme attributes that resolve to color resources. See the following sections to know how to apply a tint to different UI components that can host icons.

### ImageView
Use the `tint` attribute to apply color tint to an ImageView's drawable. Since the Android framework support for `tint` starts from **API21+**, the custom attribute namespace could be used for backwards compatibility.
```xml
<ImageView
    ...
    android:src="@drawable/ic_add_alarm_button"
    app:tint="@android:color/white"
    android:tint="@android:color/white"/> // OK to use just the framework one too since most MSFT apps are API21+

```
By code, use `ImageViewCompat` from the [AndroidX core library](https://developer.android.com/jetpack/androidx/releases/core):
```java
ImageViewCompat.setImageTintList(imageView, ColorStateList.valueOf(Color.WHITE));

// OK to use just the framework one too since most MSFT apps are API21+
imageView.setImageTintList(ColorStateList.valueOf(Color.WHITE));
```
### TextView compound drawable
Use the `drawableTint` attribute to apply color tint to a TextView's compound drawable icon. Since the Android framework support for `drawableTint` starts from **API24+**, the custom attribute namespace could be used for backwards compatibility.
```xml
<TextView
    ...
    android:text="Done"
    android:drawableStart="@drawable/ic_add_alarm_button"
    app:drawableTint="@android:color/white"/>
```
By code, use `TextViewCompat` from the [AndroidX core library](https://developer.android.com/jetpack/androidx/releases/core):
```java
TextViewCompat.setCompoundDrawableTintList(textView, ColorStateList.valueOf(Color.WHITE));
```

### Menu item icon
Use the `iconTint` attribute to apply color tint to a MenuItem's icon. Since the Android framework support for `iconTint` starts from **API26+**, the custom attribute namespace could be used for backwards compatibility.
```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">
    <item
        android:id="@+id/menu_done"
        android:icon="@drawable/ic_add_alarm_button"
        android:title="Done"
        app:iconTint="@android:color/white"
        app:showAsAction="always"/>
</menu>
```
By code, use `MenutItemCompat` from the [AndroidX core library](https://developer.android.com/jetpack/androidx/releases/core):
```java
@Override
public boolean onCreateOptionsMenu(Menu menu) {
    ...
    MenuItem doneItem = menu.findItem(R.id.menu_done);
    MenuItemCompat.setIconTintList(doneItem, ColorStateList.valueOf(Color.WHITE));
    ...
}
```

### Drawable
Drawables can be tinted by using `DrawableCompat` from the [AndroidX core library](https://developer.android.com/jetpack/androidx/releases/core):
```java
Drawable icon = ContextCompat.getDrawable(this, R.drawable.ic_add_alarm_button);

// Tint drawable with a single color
DrawableCompat.setTint(icon, Color.WHITE);
// Tint drawable with a color state list
DrawableCompat.setTintList(icon, ContextCompat.getColorStateList(this, R.color.white_selector));
```

## Contact
Please feel free to reach out to the following points of contact with questions or requests.
* [Manikandan](mailto:rsmani.kand97@gmail.com) - Android
