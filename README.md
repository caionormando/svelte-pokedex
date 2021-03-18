# Image predicter for visually impaired people

This project contains a Pokédex SPA including all the latest pokémon generations.

## Flow diagram

The project schematics are the ones described below:

![diagramFlow](https://github.com/caionormando/image-predicter-for-visual-impairment/blob/master/image-predicter/Resources/Diagram%20flow.png)

## Demonstration

By aiming the camera to any object and clicking on predict, this app takes a snapshot and send it to Clarifai API in order to retrieve the possible results for the images. Then, the results and their prediction chances are displayed below.

![demonstration](https://github.com/caionormando/image-predicter-for-visual-impairment/blob/master/image-predicter/Resources/demonstration.gif)

## Resources
* Angular 9
* RxJS 6.5
* HTML5
* SCSS
* Javascript
* Bootstrap
* Clarifai general mode API
* Ngx-Spinner
* Ngx-Webcam

## Issues
Important: this app is served on a secure context using https:// or on localhost, for modern browsers to permit WebRTC/UserMedia access. This is a requirement from Ngx-Webcam.
 
## Status
Beta