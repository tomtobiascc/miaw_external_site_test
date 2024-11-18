<html>
    <body>
        <script type='text/javascript'>
        	function initEmbeddedMessaging() {
        		try {
        			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'
        			embeddedservice_bootstrap.init(
        				'00DV9000001CZRF',
        				'Messaging_for_Verified_Users',
        				'https://billcom--messaging.sandbox.my.site.com/ESWMessagingforVerified1730416007264',
        				{
        					scrt2URL: 'https://billcom--messaging.sandbox.my.salesforce-scrt.com'
        				}
        			);
        		} catch (err) {
        			console.error('Error loading Embedded Messaging: ', err);
        		}
        	};
        </script>
        <script type='text/javascript' src='https://billcom--messaging.sandbox.my.site.com/ESWMessagingforVerified1730416007264/assets/js/bootstrap.min.js' onload='initEmbeddedMessaging()'></script>
        
        <script>
            var userId = "005V9000004FWy3IAG";
            
            function callPrechatAPI() {
                if(userId == undefined) {userId = ""}
            	console.log ('Passing HiddenPrechatUserId = userId (currently Logged In User Id, or ' + userId + ')');
                sessionStorage.setItem("userId", userId);
             // Send it!
             //	embeddedservice_bootstrap.prechatAPI.setHiddenPrechatFields({'userId' : userId});
            }
            function trapButtonClick() {
            	console.log ('Looking for embeddedMessagingConversationButton...');
            	var b = document.getElementById('embeddedMessagingConversationButton');
            	if (b != null) {
            	console.log ('Found it, attaching to onClick event');
            	b.addEventListener ('click', callPrechatAPI);
             } else {
            	console.log ('No button yet; wait a second and try again');
            	setTimeout (trapButtonClick, 1000);
             }
            }
            window.addEventListener("onEmbeddedMessagingReady", () => {
             console.log ('Received the onEmbeddedMessagingReady event...');
             embeddedservice_bootstrap.userVerificationAPI.setIdentityToken({
    identityTokenType: "JWT", identityToken: "eyJraWQiOiIxMjM0NSIsImFsZyI6IlJTMjU2In0.eyJpc3MiOiJ0ZXN0SXNzdWVyIiwic3ViIjoidXNlcjEiLCJleHAiOjE3MzI1NTY1MTUsImlhdCI6MTczMTk1NjUxNX0.Qy7li1gw4ihdqsPxQBo0VQbb6iN48bxknpyYNRkpvpPmrlEvfOsr1Y0BAy9hZMq8Ganafw6BpS6732t-J3IWCFbin665nw-IPexBNhHvAwzT97G85_CmUZTtpMHi-6p2eMz8-Yol41mDa6f19mUh1Ow-oaR-oEmIG1Rqn8z8TyK-88uuWDCQiYmyxK8uUVYx580-jz41ijQs-r_9fcBK9IwLCLoborC1autXjX747jFlG4y0iNfdp7JuQyRw6T1nke6aN2oNsG6JKKtATwuZKhJfIsRiru8NrDxbViiQMnUoGnvGRgUvwGgVl1cWpsfuLGnsbs3tHWjLSXXV9VY_zA"});
    

            embeddedservice_bootstrap.prechatAPI.setVisiblePrechatFields({
                "userId": {
                    "value": "005V9000004FWy3IAG",
                    "isEditableByEndUser": false
                }
            });
             callPrechatAPI();
            });
            window.addEventListener ("load", trapButtonClick);
        </script>
    </body>
</html>
