# Steps to creating a CMS:

## Phase Zero

Decide what Tatvum can define as a minimum viable product. Stick with as a roadmap. Make this part such that it need not be edited for every project - both with respect to UI of the backend and the backend of the backend.

## Continuous improvement

Decide what new features are required to be added to the CMS that we have created. Add these features on client request. 
**
**
**Eg.**

* Lead Management system
* Print a pdf of the screen
* Currency converter**
**

**
**
Below is a short list created for the purpose of simplification:
**
**
**For a Skeleton website**

* Login Module
* User Management
* SEO
* General Settings of the site
* Page Management
* Navigation
* Contact Form & Subscribe Now

**Time required: **20 days
_________________________________________________________

**For a Content driven website**
* Post Creation
* Gallery/ DAM
* Temporary Storage
* Category management
* Comments
* Integration with Mailchimp and/or other SMTP service providers
* Perma-links/URL structure
* Other widgets & their settings Eg. social share, social widget plugins, comments etc.

**
**
**Time required: **20 days
_________________________________________________________

**For an ecommerce website**
* Product CSV uploader
* Inventory manager
* Order management & response
* Coupons
* Reporting Dashboard (for Orders, Customers, Stocks and if possible Most Selling & Most Visited)
* Shipping

**Time required: **20 days
_________________________________________________________

Product CSV uploader
Inventory manager
Order management & response
Coupons
Reporting Dashboard (for Orders, Customers, Stocks and if possible Most Selling & Most Visited)
Shipping

## User Flow:

A user arrives at the CMS backend. 

**Login**

He is asked to login using an login via FB/Google OR email id/username and password. 
If he doesn’t have login credentials, he can choose to register. 
* He can sign up by Facebook, Google OR via email id. 
* In the case of email id mandatory fields will be at least First, Last names, email id and password. He might be asked to enter his password twice to ensure that the password entered in both fields match.

If he has login credentials and has forgotten them, 
* If he has forgotten only his password, he can choose to reset his password. In that case he is shown a screen with 2 fields - to enter the password twice. The password strength can be quantified as a score.
* If he has forgotten his username/email id used, he can choose to answer a few questions/ give his most likely used email id. The system will verify if the email id is in our user base and revert with “Oh its you.. we have auto generated an auto response email with a 4 digit pin/link that allows you to reset your password.”

**User Management**
1. Level 0 - Administrator
2. Level 1 - Creator
3. Level 2 - Editor
4. Level 3 - Contributor
5. Level 4 - Subscriber

**SEO**
User visits a tab that reads SEO OR visits the section on a page that is for SEO data entry. In that section he is prompted with a form that takes in inputs. OG:URL will be pre-populated by the URL of the page and OG:IMAGE will be selected from a grid of options.**
**
|  **Google Meta** | **Facebook OG meta** | **Twitter Meta** | **Content example** |
|-----|-----|-----|-----|
|  charset = utf-8 | - | - | 
 |
|  Http-equiv = X-UA-Compatible | - | - | IE=9 |
|  Viewport | - | - | width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no |
|  title | Og:title | Twitter:title | The Rock |
|  description | Og:description | Twitter:description | 
 |
|  
 | Og:image | Twitter:image | http://ia.media-imdb.com/images/rock.jpg |
|  
 | Og:url | 
 | http://www.imdb.com/title/tt0117500/ |
|  Keywords | 
 | 
 | Some, important, words, from, the, site |
|  Robots | 
 | 
 | No-follow, index |
|  Canonical | 
 | 
 | 
 |
**
**
Schema creator/ entry block.
Google AMP & Facebook Instant Articles

**General Settings of the site**
1. Site name (this can be appended to the end of the meta title as an option)
2. Favicon of the site
3. Google Analytics ID for the site
4. Icons set for the site

|  icon.png | 192 x 192 |
|-----|-----|
|  ios-icon.png | 192 x 192 |
|  touch-icon-iphone.png | 192 x 192 |
|  touch-icon-ipad.png | 76 x 76 |
|  touch-icon-iphone-retina.png | 120 x 120 |
|  touch-icon-ipad-retina.png | 152 152 |
|  icon_largetile.png | 310 x 310 |
|  icon_smalltile.png | 70 x 70 |
|  icon_mediumtile.png | 150 x 150 |
|  icon_widetile.png | 310 x 150 |

1. Theme colour for the site

|  theme-color | #56BBDC |
|-----|-----|

1. URL structure pattern - domain.com/hyphenated-title.html OR domain.com/year/month/date/hyphenated-title.html OR domain.com/id=30 
2. Timezone (for timestamp storage and display)
3. Date & time format
4. Mobile app URL for Google play store and App Store (to enable view/open prompt on mobile version of site - <meta name="apple-itunes-app" content="app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL"> <meta name="google-play-app" content="app-id=com.mygood.id"> <link rel="stylesheet" href="jquery.smartbanner.css" type="text/css" media="screen"> <script src="//ajax.googleapis.com/ajax/libs/jquery/1.8/jquery.min.js"></script> <script src="jquery.smartbanner.js"></script>  <script>          $.smartbanner({

			title: 'My good title',
			author: 'My smart author'
		});
	</script>**
**
**
**
**Forms**
Three kinds of forms are needed for most business cases. 
1. Subscribe to the newsletter form - modal/popup - will lead you to a thank you page on filling OR will trigger an email to confirm subscription on click of which user will then be thanked for subscribing, and a email confirmation of subscription will be triggered OR will trigger a thank you for subscribing email
2. Get this freebie form - to be inserted into a certain page as a opening roadblock or closing roadblock or on a landing page - will lead you to the freebie on filling or to a landing page which has the link to the freebie
3. Contact Us form - to be used in the footer or on a dedicated landing page - on filling of which user can be led to a thank you page and an email will be sent to the client regarding the entry AND/OR a mail will be sent to user thanking him for filling the form.

Basically, on filling of a form, the end user can receive emails with a custom appearance AND/OR be led to a landing page with a custom appearance AND/OR be asked to confirm his identity via email.

There must be a place to update the default email ids that must receive the details from forms

**Navigation**

**Contact Support**

