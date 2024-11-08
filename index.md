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
    identityTokenType: "JWT", identityToken: "eyJraWQiOiIxMjM0NSIsImFsZyI6IlJTMjU2In0.eyJpc3MiOiJ0ZXN0SXNzdWVyIiwic3ViIjoidXNlcjEiLCJleHAiOjE3MzE2ODgxODIsImlhdCI6MTczMTA4ODE4Mn0.hqorT2YdQEDroxdIiHmbP4WrpcErWJ-yNrv_EqJIOCFocG_YkPdiKpvKvkiaga8EmpTHqMG63vMlIv3849ILHcgGFv9Czfis_O-NnLKR3GIbJXwuxsVI_gsEtGFfNM_hQB_tZHZsklX1Hl-RU75-1Iw6Y-sRPPPU-96SjqqbXJml_QBItK9y2OUvYReDB9IEBCuDvHfmMxCYEZNbbx-_W1PHzgX-q8P_OSly90pIRdTrxqa3L_actp9wNJj4wDF9hS3hTikmCsenT7pwmE92d6KBMqReGx3wmC9ihGz9ZnEtFnmmWy7uKGWAeYBfgqoWp5vnXk3F6MDNoVS4moN4Cw"});
    

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
