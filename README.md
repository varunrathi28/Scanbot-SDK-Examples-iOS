# Scanbot-SDK-Examples-iOS

Scanbot SDK for iOS is a simple to use high level API, providing a collection of classes and functions 
for scanning and processing documents from your mobile device's camera or other image sources like your photo library.

Boost your iOS app with the powerful and convenient document scanning and processing features that also drive the #1
scanning app in the iOS app store: Scanbot Pro.

Scanbot SDK consists of a bunch of modules, each individually licensable or avalaible in license packages.

Currently the following modules are available
- Document detection in digital images
- User interface for guided, automatic document scanning using the document detection module
- Image processing for rotating, cropping, filtering and perspective correction, optimized for the needs of document 
scanning
- PDF creation, merge a collection of processed or unprocessed document images and write them into a PDF document with 
one page per image
- Optical character recognition, recognize text in document images and create searchable PDF documents with 
selectable text
- Payform recognition, detect and recognize SEPA payforms on images and extract the important data fields via OCR

Along with the demo app this repository comes with the full Scanbot SDK:
https://github.com/doo/Scanbot-SDK-Examples-iOS/tree/master/DocumentDetectionDemo/ScanbotSDK

Documentation can be found here:
https://github.com/doo/Scanbot-SDK-Examples-iOS/tree/master/DocumentDetectionDemo/ScanbotSDK/Documentation

If you need further information or are interested in licensing Scanbot SDK please contact us 
by mail to sdk@scanbot.io. When sending a mail please provide your apps bundle identifier to us so we can
generate development or test licenses for you.

This is a trial version and will only work for 1 minute (if you require a trial license which works for a longer period of time please contact us).
We are constantly updating and evolving the SDK and it is no final product.
The SDK with a trial license should only be tested in a experimental setting and it is not developed to be integrated into your live products.


##### Changelog version 1.0.5:

###### SBSDKScannerViewControllerDelegate
Changed signatures of following methods
```
- (UIView *)viewForDetectionStatus:(SBSDKDocumentDetectionStatus)status forScannerController:(SBSDKScannerViewController *)controller;
- (UIButton *)shutterButtonForScannerController:(SBSDKScannerViewController *)controller;
- (UIColor *)polygonColorForDetectionStatus:(SBSDKDocumentDetectionStatus)status forScannerController:(SBSDKScannerViewController *)controller;
```
to start them all with scannerController:...


Changed signature of 
```
- (void)scannerController:(SBSDKScannerViewController *)controller didCaptureImage:(CMSampleBufferRef)sampleBuffer;
```
Instead of CMSampleBufferRef it delivers an UIImage.


Added new method for custom drawing of detected document polygon
```
- (void)scannerController:(SBSDKScannerViewController *)controller drawPolygonPoints:(NSArray *)pointValues withDetectionStatus:(SBSDKDocumentDetectionStatus)detectionStatus onLayer:(CAShapeLayer *)layer;
```


###### SBSDKScannerViewController
- Fixed a bug with empty images/samplebuffers
- Removed property cameraControlsHidden and replaced it by two separate properties shutterButtonHidden and detectionStatusHidden

###### Licensing
- Licenses can now be valid for iOS, Android or both




##### Changelog version 1.0.6:

###### SBSDKScannerViewController
- Fixed a bug that prevented displaying the detection statuses for poor light and noise
- Added properties acceptedSizeScore and acceptedAngleScore, allowing you to alter the acceptance parameters for automatic shutter release (e.g. more perspective distortion or smaller document size)