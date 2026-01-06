
.. meta::
   :description: Complete guide to Flutter Widgets (StatelessWidget, StatefulWidget, examples).
   :keywords: Flutter, Widgets, StatelessWidget, StatefulWidget, Dart, Tutorial, sherullah, site, override, build, sherullah.com

Widget 
======

**Widget** is the **basic building block** of the user interface (UI).
Everything you see on the screen — from a simple **text label** to a **button**, a **layout structure**, or even an entire **screen** — is a **widget.** 
A **widget** describes **how an element should look and behave**. It tells Flutter **what to draw** and **how to respond to user interactions.**

**Two Main Types of Widgets**

**1.	StatelessWidget**

    •	Does not change once built.

    •	Used for static parts of the UI.

    •	Example: a Text, Icon, or Container that doesn’t update dynamically.

.. code-block:: dart 

    class MyText extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Text('Hello Flutter!');
      }
    }

**2.	StatefulWidget**

    •	Can change its appearance in response to user interaction or data updates.

    •	Maintains a mutable state using a separate State object.

.. code-block:: dart 

    class CounterWidget extends StatefulWidget {
      @override
      State<CounterWidget> createState() => _CounterWidgetState();
    }

    class _CounterWidgetState extends State<CounterWidget> {
      int count = 0;

        @override
        Widget build(BuildContext context) {
            return Column(
                children: [
                Text('Count: $count'),
                ElevatedButton(
                    onPressed: () {
                        setState(() {
                           count++;
                        });
                    },
                    child: Text('Increment'),
                ),
                ],
            );
        }
    }

.. ======Advertisment bellow======
..
  .. include:: /_ads/bottom_ad.rst


.. 
  .. raw:: html
    <script src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
    <ins class="adsbygoogle"
          style="display:block"
          data-ad-client="ca-pub-xxxxxx"
          data-ad-slot="xxxxxx"
          data-ad-format="auto"></ins>
    <script>
          (adsbygoogle = window.adsbygoogle || []).push({});
    </script>


   
.. 
  .. raw:: html
    <a href="https://www.amazon.com/dp/1801072647?_encoding=UTF8&pd_rd_w=7T9Wf&content-id=amzn1.sym.476b1b7d-c787-4147-8a3c-fdef209103a1&pf_rd_p=476b1b7d-c787-4147-8a3c-fdef209103a1&pf_rd_r=98EAVTNVV2CD6YHZFAP3&pd_rd_wg=8lGud&pd_rd_r=5c02368b-db9a-4133-9acb-32f8e4203183&linkCode=ll1&tag=sherullahblog-20&linkId=5f7699ca7b000d576d6e634761c22519&language=en_US&ref_=as_li_ss_tl"
        target="_blank"
        rel="nofollow noopener"
        style="
          background:#ff9900;
          color:white;
          padding:10px 16px;
          border-radius:6px;
          font-weight:600;
          text-decoration:none;">
        ► View This Book on Amazon
    </a>