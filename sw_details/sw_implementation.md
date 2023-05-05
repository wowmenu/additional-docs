# Implementation Details

## Project Dependencies

<pre class="yaml" style="font-family:monospace;"><span style="color: #007F45;">dependencies</span>:<span style="color: #007F45;">
    flutter</span>:<span style="color: green;">
        sdk</span><span style="font-weight: bold; color: brown;">: </span>flutter
<span style="color: green;">
    cupertino_icons</span><span style="font-weight: bold; color: brown;">: </span>^1.0.2<span style="color: green;">
    get</span><span style="font-weight: bold; color: brown;">: </span>^4.6.5<span style="color: green;">
    firebase_auth</span><span style="font-weight: bold; color: brown;">: </span>^4.2.6<span style="color: green;">
    cloud_firestore</span><span style="font-weight: bold; color: brown;">: </span>^4.3.2<span style="color: green;">
    firebase_core</span><span style="font-weight: bold; color: brown;">: </span>^2.8.0<span style="color: green;">
    google_sign_in</span><span style="font-weight: bold; color: brown;">: </span>^5.4.4<span style="color: green;">
    url_launcher</span><span style="font-weight: bold; color: brown;">: </span>^6.1.9<span style="color: green;">
    flutter_signin_button</span><span style="font-weight: bold; color: brown;">: </span>^2.0.0<span style="color: green;">
    flutter_osm_plugin</span><span style="font-weight: bold; color: brown;">: </span>^0.40.3<span style="color: green;">
    http</span><span style="font-weight: bold; color: brown;">: </span>^0.13.5<span style="color: green;">
    flutter_svg</span><span style="font-weight: bold; color: brown;">: </span>^1.1.6<span style="color: green;">
    google_fonts</span><span style="font-weight: bold; color: brown;">: </span>^4.0.3<span style="color: green;">
    carousel_slider</span><span style="font-weight: bold; color: brown;">: </span>^4.2.1<span style="color: green;">
    carousel_indicator</span><span style="font-weight: bold; color: brown;">: </span>^1.0.6<span style="color: green;">
    bottom_navy_bar</span><span style="font-weight: bold; color: brown;">: </span>^6.0.0<span style="color: green;">
    geoflutterfire2</span><span style="font-weight: bold; color: brown;">: </span>^2.3.15<span style="color: green;">
    geolocator</span><span style="font-weight: bold; color: brown;">: </span>^9.0.2<span style="color: green;">
    material_tag_editor</span><span style="font-weight: bold; color: brown;">: </span>^0.1.2</pre>

## Project Architecture

This project follows the GetX architecture pattern which consists of Models, Views, Controllers, and Services.

## Folder Structure

```
├── assets
│   ├── Frame-1.svg
│   ├── Frame-2.svg
│   ├── Frame-3.svg
│   └── icons
│       ├── bx_bxs-star.svg
│       ├── cooker.svg
│       ├── filter_icon.svg
│       ├── google.svg
│       ├── ic_baseline-location-on.svg
│       ├── non-veg-icon.svg
│       └── veg-icon.svg
├── controllers
│   └── app_logic_controller.dart
├── firebase_options.dart
├── generated_plugin_registrant.dart
├── main.dart
├── models
│   ├── location_model.dart
│   └── restaurant_model.dart
├── utils
│   ├── formatters.dart
│   ├── size_util.dart
│   └── theme.dart
└── views
    ├── app_root.dart
    ├── components
    │   ├── buttons.dart
    │   ├── error_screen.dart
    │   ├── header.dart
    │   ├── informationBox.dart
    │   ├── location_selector.dart
    │   ├── menuItemTile.dart
    │   └── restaurantInformationTile.dart
    ├── contact_us_page.dart
    ├── landing_page.dart
    ├── partner_views
    │   ├── add_menu_form.dart
    │   ├── buisness_control_root.dart
    │   ├── partner_onboarding_form.dart
    │   ├── update_menu_card.dart
    │   └── update_notice_board.dart
    ├── restaurant_details_view.dart
    └── sub_views
        ├── home.dart
        ├── profile.dart
        └── saved_places.dart
```

## Models

### User Model
<pre class="javascript" style="font-family:monospace;">AppUser <span style="color: #009900;">&#123;</span>
    uid<span style="color: #339933;">:</span> str<span style="color: #339933;">,</span>
    email<span style="color: #339933;">:</span> str<span style="color: #339933;">,</span>
    photo_url<span style="color: #339933;">:</span> str
<span style="color: #009900;">&#125;</span></pre>

### Owner Model
<pre class="java" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">class</span> <span style="color: #003399;">Owner</span> <span style="color: #009900;">&#123;</span>
  <span style="color: #003399;">String</span><span style="color: #339933;">?</span> name<span style="color: #339933;">;</span>
  <span style="color: #003399;">String</span><span style="color: #339933;">?</span> email<span style="color: #339933;">;</span>
  <span style="color: #003399;">String</span><span style="color: #339933;">?</span> uid<span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #003399;">Owner</span><span style="color: #009900;">&#40;</span><span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">name</span>, <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">email</span>, <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">uid</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #003399;">Owner</span>.<span style="color: #006633;">fromMap</span><span style="color: #009900;">&#40;</span>Map<span style="color: #339933;">&lt;</span><span style="color: #003399;">String</span>, dynamic<span style="color: #339933;">&gt;</span> data<span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    name <span style="color: #339933;">=</span> data<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;name&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    email <span style="color: #339933;">=</span> data<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;email&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    uid <span style="color: #339933;">=</span> data<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;uid&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
&nbsp;
  Map<span style="color: #339933;">&lt;</span><span style="color: #003399;">String</span>, dynamic<span style="color: #339933;">&gt;</span> toMap<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    <span style="color: #000000; font-weight: bold;">return</span> <span style="color: #009900;">&#123;</span><span style="color: #0000ff;">&quot;name&quot;</span><span style="color: #339933;">:</span> name, <span style="color: #0000ff;">&quot;email&quot;</span><span style="color: #339933;">:</span> email, <span style="color: #0000ff;">&quot;uid&quot;</span><span style="color: #339933;">:</span> uid<span style="color: #009900;">&#125;</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
&nbsp;
  @override
  <span style="color: #003399;">String</span> toString<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    <span style="color: #000000; font-weight: bold;">return</span> <span style="color: #0000ff;">'Owner{name: $name, email: $email, uid: $uid}'</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
<span style="color: #009900;">&#125;</span></pre>

### FoodItem Model
<pre class="java" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">class</span> FoodItem <span style="color: #009900;">&#123;</span>
  <span style="color: #003399;">String</span><span style="color: #339933;">?</span> name<span style="color: #339933;">;</span>
  <span style="color: #003399;">String</span><span style="color: #339933;">?</span> description<span style="color: #339933;">;</span>
  <span style="color: #000066; font-weight: bold;">double</span><span style="color: #339933;">?</span> price<span style="color: #339933;">;</span>
  <span style="color: #000066; font-weight: bold;">int</span><span style="color: #339933;">?</span> pos<span style="color: #339933;">;</span>
&nbsp;
&nbsp;
  FoodItem<span style="color: #009900;">&#40;</span><span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">name</span>, <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">description</span>, <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">price</span>, <span style="color: #009900;">&#91;</span><span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">pos</span> <span style="color: #339933;">=</span> <span style="color: #cc66cc;">0</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
  FoodItem.<span style="color: #006633;">fromMap</span><span style="color: #009900;">&#40;</span>Map<span style="color: #339933;">&lt;</span><span style="color: #003399;">String</span>, dynamic<span style="color: #339933;">&gt;</span> data<span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    name <span style="color: #339933;">=</span> data<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;name&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    description <span style="color: #339933;">=</span> data<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;desc&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    price <span style="color: #339933;">=</span> data<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;price&quot;</span><span style="color: #009900;">&#93;</span>.<span style="color: #006633;">toDouble</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    pos <span style="color: #339933;">=</span> data<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;pos&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
&nbsp;
  Map<span style="color: #339933;">&lt;</span><span style="color: #003399;">String</span>, dynamic<span style="color: #339933;">&gt;</span> toMap<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    <span style="color: #000000; font-weight: bold;">return</span> <span style="color: #009900;">&#123;</span>
      <span style="color: #0000ff;">&quot;name&quot;</span> <span style="color: #339933;">:</span> name,
      <span style="color: #0000ff;">&quot;desc&quot;</span> <span style="color: #339933;">:</span> description,
      <span style="color: #0000ff;">&quot;price&quot;</span> <span style="color: #339933;">:</span> price,
      <span style="color: #0000ff;">&quot;pos&quot;</span> <span style="color: #339933;">:</span> pos
    <span style="color: #009900;">&#125;</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
&nbsp;
  @override
  <span style="color: #003399;">String</span> toString<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    <span style="color: #000000; font-weight: bold;">return</span> <span style="color: #0000ff;">'MenuItem{name: $name, description: $description, price: $price, pos: $pos}'</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
<span style="color: #009900;">&#125;</span></pre>


### Menu Model
<pre class="java" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">class</span> <span style="color: #003399;">Menu</span> <span style="color: #009900;">&#123;</span>
  List<span style="color: #339933;">&lt;</span>FoodItem<span style="color: #339933;">&gt;</span> items <span style="color: #339933;">=</span> <span style="color: #009900;">&#91;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #003399;">Menu</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #003399;">Menu</span>.<span style="color: #006633;">fromList</span><span style="color: #009900;">&#40;</span><span style="color: #003399;">List</span> data<span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    items <span style="color: #339933;">=</span> data.<span style="color: #006633;">map</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#40;</span>e<span style="color: #009900;">&#41;</span> <span style="color: #339933;">=&gt;</span> FoodItem.<span style="color: #006633;">fromMap</span><span style="color: #009900;">&#40;</span>e<span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span>.<span style="color: #006633;">toList</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
&nbsp;
  List<span style="color: #339933;">&lt;</span>Map<span style="color: #339933;">&lt;</span><span style="color: #003399;">String</span>, dynamic<span style="color: #339933;">&gt;&gt;</span> mapCompatible<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    <span style="color: #000000; font-weight: bold;">return</span> items.<span style="color: #006633;">map</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#40;</span>e<span style="color: #009900;">&#41;</span> <span style="color: #339933;">=&gt;</span> e.<span style="color: #006633;">toMap</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span>.<span style="color: #006633;">toList</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
&nbsp;
  @override
  <span style="color: #003399;">String</span> toString<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    <span style="color: #000000; font-weight: bold;">return</span> <span style="color: #0000ff;">'Menu{items: $items}'</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
<span style="color: #009900;">&#125;</span></pre>


### Restaurant Model
<pre class="java" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">class</span> Restaurant <span style="color: #009900;">&#123;</span>
  <span style="color: #003399;">String</span><span style="color: #339933;">?</span> address<span style="color: #339933;">;</span>
  ApplicationStatus<span style="color: #339933;">?</span> applicationStatus<span style="color: #339933;">;</span>
  <span style="color: #003399;">Owner</span><span style="color: #339933;">?</span> owner<span style="color: #339933;">;</span>
&nbsp;
  bool<span style="color: #339933;">?</span> isNonVeg<span style="color: #339933;">;</span>
  bool<span style="color: #339933;">?</span> isVeg<span style="color: #339933;">;</span>
  GeoFirePoint<span style="color: #339933;">?</span> location<span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #003399;">String</span><span style="color: #339933;">?</span> name<span style="color: #339933;">;</span>
  <span style="color: #003399;">String</span><span style="color: #339933;">?</span> mobile<span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #003399;">Menu</span><span style="color: #339933;">?</span> menu <span style="color: #339933;">=</span> <span style="color: #003399;">Menu</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #000066; font-weight: bold;">int</span><span style="color: #339933;">?</span> seatingCapacity<span style="color: #339933;">;</span>
  <span style="color: #003399;">String</span><span style="color: #339933;">?</span> status<span style="color: #339933;">;</span>
&nbsp;
  List<span style="color: #339933;">&lt;</span>String<span style="color: #339933;">&gt;</span> tags <span style="color: #339933;">=</span> <span style="color: #009900;">&#91;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
&nbsp;
&nbsp;
  <span style="color: #003399;">String</span><span style="color: #339933;">?</span> noticeBoard<span style="color: #339933;">;</span>
&nbsp;
  Restaurant.<span style="color: #006633;">onBoardingInstance</span><span style="color: #009900;">&#40;</span>
      <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">owner</span>,
      <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">name</span>,
      <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">mobile</span>,
      <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">address</span>,
      <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">location</span>,
      <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">isVeg</span>,
      <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">isNonVeg</span>,
      <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">seatingCapacity</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    applicationStatus <span style="color: #339933;">=</span>
        ApplicationStatus<span style="color: #009900;">&#40;</span>Status.<span style="color: #006633;">under_verification</span>, DateTime.<span style="color: #006633;">now</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    status <span style="color: #339933;">=</span> Status.<span style="color: #006633;">blocked</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
&nbsp;
  Restaurant.<span style="color: #006633;">fromFirestoreDocument</span><span style="color: #009900;">&#40;</span>
      DocumentSnapshot<span style="color: #339933;">&lt;</span>Map<span style="color: #339933;">&lt;</span><span style="color: #003399;">String</span>, dynamic<span style="color: #339933;">&gt;&gt;</span> documentSnapshot<span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    Map<span style="color: #339933;">&lt;</span><span style="color: #003399;">String</span>, dynamic<span style="color: #339933;">&gt;</span> dataFromDoc <span style="color: #339933;">=</span> documentSnapshot.<span style="color: #006633;">data</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">!;</span>
&nbsp;
    address <span style="color: #339933;">=</span> dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;address&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    applicationStatus <span style="color: #339933;">=</span>
        ApplicationStatus.<span style="color: #006633;">fromMap</span><span style="color: #009900;">&#40;</span>dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;application_status&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
    isVeg <span style="color: #339933;">=</span> dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;isVeg&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    isNonVeg <span style="color: #339933;">=</span> dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;isNonVeg&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
&nbsp;
    GeoPoint locCoord <span style="color: #339933;">=</span> <span style="color: #009900;">&#40;</span>dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;location&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;geopoint&quot;</span><span style="color: #009900;">&#93;</span> as GeoPoint<span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    location <span style="color: #339933;">=</span> GeoFirePoint<span style="color: #009900;">&#40;</span>locCoord.<span style="color: #006633;">latitude</span>, locCoord.<span style="color: #006633;">longitude</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
    name <span style="color: #339933;">=</span> dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;name&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    mobile <span style="color: #339933;">=</span> dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;mobile&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
&nbsp;
    owner <span style="color: #339933;">=</span> <span style="color: #003399;">Owner</span>.<span style="color: #006633;">fromMap</span><span style="color: #009900;">&#40;</span>dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;owner&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
    seatingCapacity <span style="color: #339933;">=</span> dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;seating_capacity&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    status <span style="color: #339933;">=</span> dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;status&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
&nbsp;
    noticeBoard <span style="color: #339933;">=</span> dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;notice_board&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
&nbsp;
    menu <span style="color: #339933;">=</span> <span style="color: #003399;">Menu</span>.<span style="color: #006633;">fromList</span><span style="color: #009900;">&#40;</span>dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;menu&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
    tags <span style="color: #339933;">=</span> <span style="color: #009900;">&#40;</span>dataFromDoc<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;tags&quot;</span><span style="color: #009900;">&#93;</span> as List<span style="color: #339933;">&lt;</span>dynamic<span style="color: #339933;">&gt;</span><span style="color: #009900;">&#41;</span>.<span style="color: #006633;">map</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#40;</span>e<span style="color: #009900;">&#41;</span> <span style="color: #339933;">=&gt;</span> e.<span style="color: #006633;">toString</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span>.<span style="color: #006633;">toList</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
&nbsp;
  Map<span style="color: #339933;">&lt;</span><span style="color: #003399;">String</span>, dynamic<span style="color: #339933;">&gt;</span> toMap<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    <span style="color: #000000; font-weight: bold;">return</span> <span style="color: #009900;">&#123;</span>
      <span style="color: #0000ff;">&quot;address&quot;</span><span style="color: #339933;">:</span> address,
      <span style="color: #0000ff;">&quot;application_status&quot;</span><span style="color: #339933;">:</span> applicationStatus<span style="color: #339933;">!</span>.<span style="color: #006633;">toMap</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span>,
      <span style="color: #0000ff;">&quot;isNonVeg&quot;</span><span style="color: #339933;">:</span> isNonVeg,
      <span style="color: #0000ff;">&quot;isVeg&quot;</span><span style="color: #339933;">:</span> isVeg,
      <span style="color: #0000ff;">&quot;location&quot;</span><span style="color: #339933;">:</span> location<span style="color: #339933;">!</span>.<span style="color: #006633;">data</span>,
      <span style="color: #0000ff;">&quot;name&quot;</span><span style="color: #339933;">:</span> name,
      <span style="color: #0000ff;">&quot;mobile&quot;</span><span style="color: #339933;">:</span> mobile,
      <span style="color: #0000ff;">&quot;owner&quot;</span><span style="color: #339933;">:</span> owner<span style="color: #339933;">!</span>.<span style="color: #006633;">toMap</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span>,
      <span style="color: #0000ff;">&quot;seating_capacity&quot;</span><span style="color: #339933;">:</span> seatingCapacity,
      <span style="color: #0000ff;">&quot;status&quot;</span><span style="color: #339933;">:</span> status,
      <span style="color: #0000ff;">&quot;tags&quot;</span> <span style="color: #339933;">:</span> tags,
      <span style="color: #0000ff;">&quot;notice_board&quot;</span> <span style="color: #339933;">:</span> noticeBoard,
      <span style="color: #0000ff;">&quot;menu&quot;</span> <span style="color: #339933;">:</span> menu<span style="color: #339933;">?</span>.<span style="color: #006633;">mapCompatible</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#125;</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
&nbsp;
  @override
  <span style="color: #003399;">String</span> toString<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    <span style="color: #000000; font-weight: bold;">return</span> <span style="color: #0000ff;">'Restaurant{address: $address, applicationStatus: $applicationStatus, owner: $owner, isNonVeg: $isNonVeg, isVeg: $isVeg, location: $location, name: $name, mobile: $mobile, menu: $menu, seatingCapacity: $seatingCapacity, status: $status, tags: $tags, noticeBoard: $noticeBoard}'</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
<span style="color: #009900;">&#125;</span>
&nbsp;</pre>

### Status Model
<pre class="java" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">class</span> ApplicationStatus <span style="color: #009900;">&#123;</span>
  <span style="color: #003399;">String</span><span style="color: #339933;">?</span> status<span style="color: #339933;">;</span>
  DateTime<span style="color: #339933;">?</span> timestamp<span style="color: #339933;">;</span>
&nbsp;
  ApplicationStatus<span style="color: #009900;">&#40;</span><span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">status</span>, <span style="color: #000000; font-weight: bold;">this</span>.<span style="color: #006633;">timestamp</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
  ApplicationStatus.<span style="color: #006633;">fromMap</span><span style="color: #009900;">&#40;</span>Map<span style="color: #339933;">&lt;</span><span style="color: #003399;">String</span>, dynamic<span style="color: #339933;">&gt;</span> data<span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    status <span style="color: #339933;">=</span> data<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;status&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    timestamp <span style="color: #339933;">=</span> data<span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;timestamp&quot;</span><span style="color: #009900;">&#93;</span>.<span style="color: #006633;">toDate</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
&nbsp;
  Map<span style="color: #339933;">&lt;</span><span style="color: #003399;">String</span>, dynamic<span style="color: #339933;">&gt;</span> toMap<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    <span style="color: #000000; font-weight: bold;">return</span> <span style="color: #009900;">&#123;</span><span style="color: #0000ff;">&quot;status&quot;</span><span style="color: #339933;">:</span> status, <span style="color: #0000ff;">&quot;timestamp&quot;</span><span style="color: #339933;">:</span> timestamp<span style="color: #009900;">&#125;</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
&nbsp;
  @override
  <span style="color: #003399;">String</span> toString<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    <span style="color: #000000; font-weight: bold;">return</span> <span style="color: #0000ff;">'ApplicationStatus{status: $status, timestamp: $timestamp}'</span><span style="color: #339933;">;</span>
  <span style="color: #009900;">&#125;</span>
<span style="color: #009900;">&#125;</span>
&nbsp;
<span style="color: #000000; font-weight: bold;">class</span> Status <span style="color: #009900;">&#123;</span>
  <span style="color: #000000; font-weight: bold;">static</span> <span style="color: #003399;">String</span> under_verification <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;under_verification&quot;</span><span style="color: #339933;">;</span>
  <span style="color: #000000; font-weight: bold;">static</span> <span style="color: #003399;">String</span> verified <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;verified&quot;</span><span style="color: #339933;">;</span>
  <span style="color: #000000; font-weight: bold;">static</span> <span style="color: #003399;">String</span> blocked <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;blocked&quot;</span><span style="color: #339933;">;</span>
  <span style="color: #000000; font-weight: bold;">static</span> <span style="color: #003399;">String</span> active <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;active&quot;</span> <span style="color: #339933;">;</span>
  <span style="color: #000000; font-weight: bold;">static</span> <span style="color: #003399;">String</span> shadow_banned <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;shadow_banned&quot;</span><span style="color: #339933;">;</span>
<span style="color: #009900;">&#125;</span></pre>


### 

## Controllers
1. AppLogicController: Handles the business logic for the app using Firebase Authentication, Database etc.


## Services
1. FirebaseService: Handles the communication with Firebase Authentication and Cloud Firestore.

<pre class="java" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">class</span> AppLogicController <span style="color: #000000; font-weight: bold;">extends</span> GetxController <span style="color: #009900;">&#123;</span>
  <span style="color: #000000; font-weight: bold;">static</span> <span style="color: #000000; font-weight: bold;">const</span> Widget _loadingWidget <span style="color: #339933;">=</span> Center<span style="color: #009900;">&#40;</span>
    child<span style="color: #339933;">:</span> CircularProgressIndicator<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span>,
  <span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #000000; font-weight: bold;">final</span> _authentication <span style="color: #339933;">=</span> FirebaseAuth.<span style="color: #006633;">instance</span><span style="color: #339933;">;</span>
  <span style="color: #000000; font-weight: bold;">final</span> _database <span style="color: #339933;">=</span> FirebaseFirestore.<span style="color: #006633;">instance</span><span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #000000; font-weight: bold;">final</span> Rx<span style="color: #339933;">&lt;</span>User<span style="color: #339933;">?&gt;</span> userFromFirebase <span style="color: #339933;">=</span> Rx<span style="color: #339933;">&lt;</span>User<span style="color: #339933;">?&gt;</span><span style="color: #009900;">&#40;</span><span style="color: #000066; font-weight: bold;">null</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
  <span style="color: #000000; font-weight: bold;">final</span> Rx<span style="color: #339933;">&lt;</span>Restaurant<span style="color: #339933;">?&gt;</span> myRestaurant <span style="color: #339933;">=</span> Rx<span style="color: #339933;">&lt;</span>Restaurant<span style="color: #339933;">?&gt;</span><span style="color: #009900;">&#40;</span><span style="color: #000066; font-weight: bold;">null</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #000000; font-weight: bold;">final</span> Rx<span style="color: #339933;">&lt;</span>LocationInfo<span style="color: #339933;">?&gt;</span> myLocation <span style="color: #339933;">=</span> Rx<span style="color: #339933;">&lt;</span>LocationInfo<span style="color: #339933;">?&gt;</span><span style="color: #009900;">&#40;</span><span style="color: #000066; font-weight: bold;">null</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
  <span style="color: #000000; font-weight: bold;">final</span> RxList<span style="color: #339933;">&lt;</span>Restaurant<span style="color: #339933;">&gt;</span> nearbyRestaurants <span style="color: #339933;">=</span> RxList<span style="color: #339933;">&lt;</span>Restaurant<span style="color: #339933;">&gt;</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#91;</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
  <span style="color: #000000; font-weight: bold;">final</span> RxList<span style="color: #339933;">&lt;</span>Restaurant<span style="color: #339933;">&gt;</span> filteredOutRestaurants <span style="color: #339933;">=</span> RxList<span style="color: #339933;">&lt;</span>Restaurant<span style="color: #339933;">&gt;</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#91;</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #000000; font-weight: bold;">static</span> <span style="color: #000066; font-weight: bold;">double</span> defaultRadius <span style="color: #339933;">=</span> <span style="color: #cc66cc;">5</span><span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #666666; font-style: italic;">/// User editable parameters</span>
  <span style="color: #000000; font-weight: bold;">final</span> Rx<span style="color: #339933;">&lt;</span>double<span style="color: #339933;">&gt;</span> radius <span style="color: #339933;">=</span> Rx<span style="color: #339933;">&lt;</span>double<span style="color: #339933;">&gt;</span><span style="color: #009900;">&#40;</span><span style="color: #cc66cc;">5</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
  <span style="color: #000000; font-weight: bold;">final</span> Rx<span style="color: #339933;">&lt;</span>FoodType<span style="color: #339933;">&gt;</span> foodType <span style="color: #339933;">=</span> Rx<span style="color: #339933;">&lt;</span>FoodType<span style="color: #339933;">&gt;</span><span style="color: #009900;">&#40;</span>FoodType.<span style="color: #006633;">any</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
  <span style="color: #000000; font-weight: bold;">final</span> Rx<span style="color: #339933;">&lt;</span>String<span style="color: #339933;">&gt;</span> query <span style="color: #339933;">=</span> Rx<span style="color: #339933;">&lt;</span>String<span style="color: #339933;">&gt;</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
&nbsp;
  <span style="color: #000066; font-weight: bold;">void</span> _actionOnFirebaseUserChange<span style="color: #009900;">&#40;</span>User<span style="color: #339933;">?</span> user<span style="color: #009900;">&#41;</span>
  <span style="color: #000066; font-weight: bold;">void</span> _actionOnQuerySnapshotChange<span style="color: #009900;">&#40;</span><span style="color: #003399;">Object</span><span style="color: #339933;">?</span> querySnapshot<span style="color: #009900;">&#41;</span>
  <span style="color: #000066; font-weight: bold;">void</span> _actionOnLocationChange<span style="color: #009900;">&#40;</span>LocationInfo<span style="color: #339933;">?</span> location<span style="color: #009900;">&#41;</span>
  <span style="color: #000066; font-weight: bold;">void</span> _actionOnNearbyRestaurantsChange<span style="color: #009900;">&#40;</span><span style="color: #003399;">Object</span><span style="color: #339933;">?</span> restaurantList<span style="color: #009900;">&#41;</span>
  <span style="color: #000066; font-weight: bold;">void</span> _actionOnRadiusChange<span style="color: #009900;">&#40;</span><span style="color: #000066; font-weight: bold;">double</span> radius<span style="color: #009900;">&#41;</span>
  <span style="color: #000066; font-weight: bold;">void</span> _actionOnFoodTypeChange<span style="color: #009900;">&#40;</span>FoodType foodType<span style="color: #009900;">&#41;</span>
  <span style="color: #000066; font-weight: bold;">void</span> _actionOnSearchQueryChange<span style="color: #009900;">&#40;</span><span style="color: #003399;">String</span> query<span style="color: #009900;">&#41;</span>
&nbsp;
  Future handleGoogleSSO<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span> 
&nbsp;
  Future handleSignOut<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span>
&nbsp;
  Future handleGoToContactUsPage<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span>
&nbsp;
  Future handleGoToPartnerOnBoardingPage<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span>
&nbsp;
  Future handleBecomeAPartner<span style="color: #009900;">&#40;</span>
      <span style="color: #003399;">String</span> name,
      <span style="color: #003399;">String</span> contact,
      <span style="color: #003399;">String</span> address,
      <span style="color: #000066; font-weight: bold;">double</span> latitude,
      <span style="color: #000066; font-weight: bold;">double</span> longitude,
      bool isVeg,
      bool isNonVeg,
      <span style="color: #000066; font-weight: bold;">int</span> seatingCapacity<span style="color: #009900;">&#41;</span>
&nbsp;
  Future handleCustomerQueryMessage<span style="color: #009900;">&#40;</span><span style="color: #003399;">String</span> message<span style="color: #009900;">&#41;</span>
&nbsp;
  Future handleNoticeBoardUpdate<span style="color: #009900;">&#40;</span><span style="color: #003399;">String</span> updatedText<span style="color: #009900;">&#41;</span>
&nbsp;
  Future handleAddNewItem<span style="color: #009900;">&#40;</span><span style="color: #003399;">String</span> name, <span style="color: #000066; font-weight: bold;">double</span> price, <span style="color: #003399;">String</span> description<span style="color: #009900;">&#41;</span>
&nbsp;
  Future handleFoodItemDelete<span style="color: #009900;">&#40;</span>FoodItem item<span style="color: #009900;">&#41;</span>
&nbsp;
  handleSetLocation<span style="color: #009900;">&#40;</span>LocationInfo locationInfo<span style="color: #009900;">&#41;</span> 
&nbsp;
  handleRadiusUpdate<span style="color: #009900;">&#40;</span><span style="color: #000066; font-weight: bold;">double</span> radius<span style="color: #009900;">&#41;</span>
&nbsp;
  handleFoodTypeUpdate<span style="color: #009900;">&#40;</span>FoodType foodType<span style="color: #009900;">&#41;</span> 
&nbsp;
  handleSearchQueryUpdate<span style="color: #009900;">&#40;</span><span style="color: #003399;">String</span> query<span style="color: #009900;">&#41;</span> 
&nbsp;
&nbsp;
  <span style="color: #000066; font-weight: bold;">double</span> getDistanceToRestaurant<span style="color: #009900;">&#40;</span>Restaurant restaurant<span style="color: #009900;">&#41;</span>
&nbsp;
  Future<span style="color: #339933;">&lt;</span><span style="color: #003399;">Position</span><span style="color: #339933;">?&gt;</span> _determinePosition<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span>
<span style="color: #009900;">&#125;</span>
&nbsp;
<span style="color: #000000; font-weight: bold;">enum</span> FoodType <span style="color: #009900;">&#123;</span> veg, nonVeg, any <span style="color: #009900;">&#125;</span>
&nbsp;</pre>