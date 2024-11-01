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
    identityTokenType: "JWT", identityToken: "eyJraWQiOiIxMjM0NSIsImFsZyI6IlJTMjU2In0.eyJpc3MiOiJ0ZXN0SXNzdWVyIiwic3ViIjoidXNlcjEiLCJleHAiOjE3MzEwMDMxNDAsImlhdCI6MTczMDQwMzE0MH0.bh5CHdQ4f3aKBTxpM65cms4lm76Fdi6-gXsKmF0j5V3cUoFx42FV-KiFv7ug-BHVfKBBmNSnL1k6zqX_oyUcFf-ySFav9fWs4tdQZYSvb_bK3OtgOlS0YJ50tOSYV3haFGdNVusQjZnbCgfZUpBuwROB0xyrTxq0vwxSC8aLIXreMN-jdABZtzvgtLM8HDO1qSnMXZiy39YAJXtFs91IqmKkAri8k_eC3lUc6gzg62HJBx-BJx3esItg1QRTUSTtyH7DeMDXPbWpV0IxloOil84ka05I9MGTFvS8ggDb3UyuETIuvy7L6MM7TJog9P2c-RPPcQ8NyBxU_7i4rRz13g"});
             callPrechatAPI();
            });
            window.addEventListener ("load", trapButtonClick);
        </script>
    </body>
</html>
