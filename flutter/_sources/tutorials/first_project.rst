First Project
================

comming soon...

Let's First import packages:

.. code-block:: dart 

  import 'package:flutter/material.dart';
  import 'package:flutter_rating_bar/flutter_rating_bar.dart';

.. code-block:: dart 
  
    class _RatingExampleState extends State<RatingExample> {
      double rating = 3.0;

      // Rating Method to set rating 
      Widget buildRatingBar() {
        return RatingBar.builder(
          initialRating: rating,
          minRating: 1,
          direction: Axis.horizontal,
          allowHalfRating: true,
          itemCount: 5,
          itemSize: 40,
          itemPadding: const EdgeInsets.symmetric(horizontal: 4.0),
          itemBuilder: (context, _) {return const Icon(Icons.star, color: Colors.amber);},
          onRatingUpdate: (value) {
            setState(() {
              rating = value;
            });
            print("Rating: $value");
          },
        );
      }

      // To show rating from given rate
      Widget buildStaticStars(double value) {
        return RatingBarIndicator(
          rating: value,
          itemSize: 30,
          itemCount: 5,
          itemBuilder: (context, _) =>
              const Icon(Icons.star, color: Colors.blue),
        );
      }
      @override
        Widget build(BuildContext context) {
          return Scaffold(
            appBar: AppBar(title: const Text('Rating Bar Example')),
            body: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                buildRatingBar(),            // interactive stars
                const SizedBox(height: 20),
                buildStaticStars(rating),    // shows the chosen value as stars
              ],
            )
          );
      }
    }

.. code-block:: dart 

  class RatingExample extends StatefulWidget {
    const RatingExample({super.key});

    @override
    State<RatingExample> createState() { return _RatingExampleState();}
  }

.. code-block:: dart 

  class MyApp extends StatelessWidget{
    const MyApp({super.key});

    @override
    Widget build(BuildContext context){
      return const MaterialApp(
        debugShowCheckedModeBanner: true,
        home: RatingExample(),
      );
    }
  }

.. code-block:: dart 

  void main(){
    runApp(const MyApp());
  }






























.. this bellow first line is call custome css class name
  .. container:: video-responsive  
    .. youtube:: YGwpnSwzq1M
        :width: 100%
        :height: 100%

.. this bellow code is embed html for youtube video for now I commente it
  .. raw:: html
    <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
      <iframe
        src="https://www.youtube.com/embed/YGwpnSwzq1M"
        style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" 
        allowfullscreen>
      </iframe>
    </div>

.. this bello is image embeded code for now I commente it
  .. image:: images/iphonescr.png
    :alt: Flutter logo
    :class: responsive-img
    :align: center
