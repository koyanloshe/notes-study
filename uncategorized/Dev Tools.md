# Dev Tools

* Consider designs that avoid images altogether, or use images sparingly. _Text-only can be beautiful_! Ask yourself, “What are visitors to my site trying to achieve? Do images help that process?”
* In the old days, it was commonplace to save headings and other text as graphics. That approach does not respond well to viewport size changes, and adds to page weight and latency. Using text as a graphic also means the text can’t be found by search engines, and isn’t accessible by screenreaders and other assistive technologies. Use “real” text where possible — Web Fonts and CSS can enable beautiful typography.
* Use CSS rather than images for gradients, shadows, rounded corners, and _background textures_, features _supported by all modern browsers_. Bear in mind, however, that CSS may be better than images, but there can still be a _processing and rendering penalty_, especially significant on mobile.
* Background images rarely work well on mobile. You can _use media queries_ to avoid background images on small viewports.
* Avoid splash screen images.
* _Use CSS for UI animations_.
* Get to know your glyphs; use _Unicode symbols and icons_ instead of images, with Web Fonts if necessary.
* Consider _icon fonts_; they are vector graphics that can be infinitely scaled, and an entire set of images can be downloaded in one font. (Be aware of _these concerns_, however.)
* The <canvas> element can be used to build images in JavaScript from lines, curves, text, and other images.
* _Inline SVG or Data URI images_ will not reduce page weight, but they can reduce latency by reducing the number of resource requests. Inline SVG has _great support on mobile and desktop browsers_, and _optimization tools_ can significantly reduce SVG size. Likewise, Data URIs are _well supported_. Both can be inlined in CSS.
* Consider using <video> instead of animated GIFs. _The video element is supported by all browsers on mobile_ (apart from Opera Mini).

For more information see _Image Optimization_ and _Eliminating and replacing images_.

