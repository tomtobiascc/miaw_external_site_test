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
    identityTokenType: "JWT", identityToken: "eyJraWQiOiIxMjM0NSIsImFsZyI6IlJTMjU2In0.eyJpc3MiOiJ0ZXN0SXNzdWVyIiwic3ViIjoidXNlcjEiLCJleHAiOjE3MzM4NTk5MTYsImlhdCI6MTczMzI1OTkxNn0.QSHDH2fEy_eHlTDl0z4TdKFS_r5271J24LEnmiWhnmXQ9HrGqmkV0EpxulDiZly7-M5Zpu7k46h19swSyTOgKUPOrYz5BKFjnV5Sc-vUrVAL9V2NHSZ87UX2QMcrij-sWwHiteXBQaCFAsOesnVGGW9lI9Gjkzpa_CfCpfKIHTaryQSBkLPeapWj6rqJL7BIUPugTSrRwqqk19VkUEuCD9ZSx5RFBLISdN9Gfp_aTR_ao8T8E7qQnB3OnyAJ5HK-zuIGEULh7rfP4HaRaIJKSO0J4wAiXqA2IEYUCQwsdJmhZjQfP-64BIc1qLFOJtw8B3e_H8EK7X9jpbhxvqu4tg"});
    

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
