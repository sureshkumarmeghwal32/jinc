# jinc
BSC NURSING FREE NOTES AND CLASSES
<!DOCTYPE html>
<html>

  <head>
    <!--
    If you are serving your web app in a path other than the root, change the
    href value below to reflect the base path you are serving from.

    The path provided below has to start and end with a slash "/" in order for
    it to work correctly.

    For more details:
    * https://developer.mozilla.org/en-US/docs/Web/HTML/Element/base

    This is a placeholder for base href that will be replaced by the value of
    the `--base-href` argument provided to `flutter build`.
  -->
    <base href="/">
    <meta charset="UTF-8">
    <meta content="IE=Edge" http-equiv="X-UA-Compatible">
    <meta name="description" content="JINC Jodhpur">
    <link rel="icon" href="icon.jpg">
    <title>JINC Classroom</title>
    <link rel="manifest" href="manifest.json">
  </head>

  <body>
    <!-- <script type="application/javascript" src="/assets/packages/flutter_inappwebview/assets/web/web_support.js"
      defer></script> -->
    <!-- <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-firestore.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-auth.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-storage.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-messaging.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-analytics.js"></script>
    <script>
      const firebaseConfig = {
        apiKey: "AIzaSyDwfoG_u-GG9YMyDI0EJAwTDABvdhRqdHs",
        authDomain: "jinc-jodhpur.firebaseapp.com",
        databaseURL: "https://jinc-jodhpur.firebaseio.com",
        projectId: "jinc-jodhpur",
        storageBucket: "jinc-jodhpur.appspot.com",
        messagingSenderId: "257057120625",
        appId: "1:257057120625:web:9dcdbbe4901c6ee7de56d0",
        measurementId: "G-1K5624B8F0"
      };

      // Initialize Firebase
      const app = firebase.initializeApp(firebaseConfig);
      const analytics = firebase.getAnalytics(app);
    </script> -->
    <!-- <div id="webview-container"></div> -->
    <script type="text/javascript">
      window.flutterWebRenderer = "html";
    </script>
    <!-- This script installs service_worker.js to provide PWA functionality to
       application. For more information, see:
       https://developers.google.com/web/fundamentals/primers/service-workers -->
    <script src="https://cdn.jsdelivr.net/npm/hls.js@latest" type="application/javascript"></script>
    <script>
      var serviceWorkerVersion = '3742643444';
      var scriptLoaded = false;
      function loadMainDartJs() {
        if (scriptLoaded) {
          return;
        }
        scriptLoaded = true;
        var scriptTag = document.createElement('script');
        scriptTag.src = 'main.dart.js';
        scriptTag.type = 'application/javascript';
        document.body.append(scriptTag);
      }

      if ('serviceWorker' in navigator) {
        // Service workers are supported. Use them.
        window.addEventListener('load', function () {
          // Wait for registration to finish before dropping the <script> tag.
          // Otherwise, the browser will load the script multiple times,
          // potentially different versions.
          var serviceWorkerUrl = 'flutter_service_worker.js?v=' + serviceWorkerVersion;
          navigator.serviceWorker.register(serviceWorkerUrl)
            .then((reg) => {
              function waitForActivation(serviceWorker) {
                serviceWorker.addEventListener('statechange', () => {
                  if (serviceWorker.state == 'activated') {
                    console.log('Installed new service worker.');
                    loadMainDartJs();
                  }
                });
              }
              if (!reg.active && (reg.installing || reg.waiting)) {
                // No active web worker and we have installed or are installing
                // one for the first time. Simply wait for it to activate.
                waitForActivation(reg.installing || reg.waiting);
              } else if (!reg.active.scriptURL.endsWith(serviceWorkerVersion)) {
                // When the app updates the serviceWorkerVersion changes, so we
                // need to ask the service worker to update.
                console.log('New service worker available.');
                reg.update();
                waitForActivation(reg.installing);
              } else {
                // Existing service worker is still good.
                console.log('Loading app from service worker.');
                loadMainDartJs();
              }
            });

          // If service worker doesn't succeed in a reasonable amount of time,
          // fallback to plaint <script> tag.
          setTimeout(() => {
            if (!scriptLoaded) {
              console.warn(
                'Failed to load app from service worker. Falling back to plain <script> tag.',
              );
              loadMainDartJs();
            }
          }, 4000);
        });
      } else {
        // Service workers not supported. Just drop the <script> tag.
        loadMainDartJs();
      }
    </script>
    <script src="https://checkout.razorpay.com/v1/checkout.js"></script>
    <script>
      function openRazorPay(pro) {
        var transRes;
        // console.log(pro);
        // console.log(pro['name']);
        // console.log(pro['price']);
        var options = {
          'key': 'rzp_live_YJZ8hnGS8ZLbBx',
          // 'key': 'rzp_live_lKxFqmGkX04Jwm',
          // 'key': 'rzp_test_vzUGCkKqRQeusH',
          'amount': parseFloat(pro['price']) * 100,
          'description': pro['name'],

          'name': "JINC EDUTECH PRIVATE LIMITED",
          "order_id": pro['orderId'],

          'handler': function (transaction) {
            // console.log(transaction);
            var url = "https://jinc-jodhpur.com/common/";
            if (transaction.razorpay_payment_id) {
              var jsonData = JSON.parse(pro['ordData']['data']['json'])
              jsonData["paGaDa"] = transaction;
              pro['ordData']['data']['json'] = JSON.stringify(jsonData);
              // pro['ordData']['data']["paSt"] = "sy";
              var xhr = new XMLHttpRequest();
              xhr.open("POST", url);
              xhr.setRequestHeader("Accept", "application/json");
              xhr.setRequestHeader("Content-Type", "application/json");
              xhr.onreadystatechange = function () {
                if (xhr.readyState === 4) {
                }
              };
              var data = btoa(JSON.stringify(pro['ordData']));
              var findata = { payload: data };
              xhr.send(JSON.stringify(findata));
              // location.reload();
            }
          },
          'prefill': {
            'name': pro['uname'],
            'email': pro['email'],
            'contact': pro['mob'],
          }
        };
        var razorpay = new Razorpay(options);
        razorpay.open();
        //  razorpay.on('payment.failed', function (response) {
        //    // console.log("response-----payment failsed");
        //    // console.log(response);

        //    var url = "http://cl.jinc-jodhpur.com/common/";
        //    pro['ordData']['data']["paDe"] = response.error;
        //    pro['ordData']['data']["paSt"] = "failed";
        //    var xhr = new XMLHttpRequest();
        //    xhr.open("POST", url);
        //    xhr.setRequestHeader("Accept", "application/json");
        //    xhr.setRequestHeader("Content-Type", "application/json");
        //    xhr.onreadystatechange = function () {
        //      if (xhr.readyState === 4) {
        //      }
        //    };
        //    var data = btoa(JSON.stringify(pro['ordData']));
        //    var findata = { payload: data };
        //    xhr.send(JSON.stringify(findata));
        //    // location.reload();

        //  })
      }
   // transactionHandler = function (transaction) {
   //   console.log(transaction);
   //   if (transaction.razorpay_payment_id) {
   //     return (transaction.razorpay_payment_id);
   //   }
   // }
 // document.getElementById('rzp-button1').onclick = function(e){
 //     rzp1.open();
 //     e.preventDefault();
 // }
    </script>
  </body>

</html>
