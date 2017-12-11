# SplitViewTest

A simple demonstation of the viewWillDisappear bug on Xcode 9.2.

The only change made beyond the Xcode generated master-detail project is:
```diff
@@ -27,6 +27,13 @@ class DetailViewController: UIViewController {
    configureView()
  }
 		  
+  override func viewWillDisappear(_ animated: Bool) {
+    super.viewWillDisappear(animated)
+    if detailDescriptionLabel == nil {
+      fatalError("viewWillDisappear called before viewControler finished initializing.")
+    }
+  }
+
   override func didReceiveMemoryWarning() {
```
