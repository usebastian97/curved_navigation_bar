# Animated Curved Navigation Bar | <img src="https://img.shields.io/badge/Build-with%20Flutter-blue"> | <img src="https://img.shields.io/badge/%20Build%20with-Dart%20Programming%20Language-blue">


Hi there, this is my new Flutter project.The code for this app has been written in Android Studio with Dart Programming Language.

## App Video

https://user-images.githubusercontent.com/76481422/120204977-15831e80-c232-11eb-8a6c-9960c6d9642b.mp4

### This will add a line like this to your package's pubspec.yaml (and run an implicit dart pub get):



```Dart
dependencies:
  curved_navigation_bar: ^0.3.7 #latest version
```

### Easy to use

```Dart
Scaffold(
  bottomNavigationBar: CurvedNavigationBar(
    backgroundColor: Colors.blueAccent,
    items: <Widget>[
      Icon(Icons.add, size: 30),
      Icon(Icons.list, size: 30),
      Icon(Icons.compare_arrows, size: 30),
    ],
    onTap: (index) {
      //Handle button tap
    },
  ),
  body: Container(color: Colors.redAccent),
)
```

### Change page programmatically 

````Dart
//State class
  int _page = 0;
  GlobalKey _bottomNavigationKey = GlobalKey();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        bottomNavigationBar: CurvedNavigationBar(
          key: _bottomNavigationKey,
          items: <Widget>[
            Icon(Icons.add, size: 30),
            Icon(Icons.list, size: 30),
            Icon(Icons.compare_arrows, size: 30),
          ],
          onTap: (index) {
            setState(() {
              _page = index;
            });
          },
        ),
        body: Container(
          color: Colors.redAccent,
          child: Center(
            child: Column(
              children: <Widget>[
                Text(_page.toString(), textScaleFactor: 30.0),
                RaisedButton(
                  child: Text('Go to page of index 0'),
                  onPressed: () {
                    //Page change using state does the same as clicking index 0 navigation button
                    final CurvedNavigationBarState navBarState =
                        _bottomNavigationKey.currentState;
                    navBarState.setPage(0);
                  },
                )
              ],
            ),
          ),
        ));
  }
````

