---
title:  "Go Flutter from Ionic Dev"
date:   2018-08-28 08:01:00 +0700
categories: [Flutter]
tags: [Ionic Framework, Ionic 4, Flutter, iOS, Android, Dart]
comments: true
---

Hi, my second Flutter article from Ionic Dev point of view.

Yes as an Ionic Developer you can easy start with **ionic start project_name <project_template>** with some boilerplate code to learn and go.

From that inspire, I try to make something like that projects (also structure). Hope it will help Ionic's Dev can quick get something new in hot trend Flutter.

![Flutter Side Menu, Tabs Struture](https://www.xmobe.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-28-at-2.48.50-PM.png){:class="img-responsive"}

## Flutter Side Menu

Github Repo: [https://github.com/xmobe-com/flutter-sidemenu][https://github.com/xmobe-com/flutter-sidemenu]

Fultter Sidemenu boilerplate help you quick create Flutter Side Menu project in a record time. It's inspired from Ionic 2/3/4 Side Menu Project. If you familiar with Ionic 2/3/4 you can feel something with the same style here.

Define your Menu list and target Page Component then everything will going on the right direction:

```dart
final List&lt;MenuItem> menuItems = &lt;MenuItem>[
  MenuItem('Home', HomePage()),
  MenuItem('List', ListPage()),
  MenuItem('Item', ItemPage()),
];
```

You can customize MenuItem and build ListTile method to upgrade your Menu with Icon or anything else you want:

```dart
class MenuItem {
  MenuItem(this.title, this.page);

  final String title;
  final StatelessWidget page;
}
```

## Flutter Tabs

Github Repo: [https://github.com/xmobe-com/flutter-tabs][https://github.com/xmobe-com/flutter-tabs]

You can customize Tab Icon and Page as you want:

```dart
appBar: AppBar(
    bottom: TabBar(
        tabs: [
            // Change Tabs here
            Tab(icon: Icon(Icons.home)),
            Tab(icon: Icon(Icons.flag)),
            Tab(icon: Icon(Icons.people)),
        ],
    ),
    title: Text('xMobe Tabs Demo'),
    ),
    body: TabBarView(
    children: [
        // Change Pages here
        HomePage(),
        FlutterPage(),
        AboutPage(),
    ],
)
```

New with Flutter?

```bash
git clone https://github.com/xmobe-com/flutter-tabs
cd flutter-tabs
flutter packages get
flutter run
```

![Flutter Side Menu, Tabs](https://www.xmobe.com/wp-content/uploads/2018/08/flutter_boilerplate.png){:class="img-responsive"}

[https://github.com/xmobe-com/flutter-sidemenu]:https://github.com/xmobe-com/flutter-sidemenu
[https://github.com/xmobe-com/flutter-tabs]:https://github.com/xmobe-com/flutter-tabs