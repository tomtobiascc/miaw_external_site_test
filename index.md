<html>
    <body>
        <script type='text/javascript'>
            function initEmbeddedMessaging() {
                try {
                    embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'

                    embeddedservice_bootstrap.init(
                        '00DV9000001CZRF',
                        'Messaging',
                        'https://billcom--messaging.sandbox.my.site.com/ESWMessaging1725555749099',
                        {
                            scrt2URL: 'https://billcom--messaging.sandbox.my.salesforce-scrt.com'
                        }
                    );
                } catch (err) {
                    console.error('Error loading Embedded Messaging: ', err);
                }
            };
        </script>
        
        <script type='text/javascript'
                src='https://billcom--messaging.sandbox.my.site.com/ESWMessaging1725555749099/assets/js/bootstrap.min.js'
                onload='initEmbeddedMessaging()'>
        </script>
        
        <script>
            var userId = "005V9000004FWy3IAG";
            function callPrechatAPI() {
                if(userId == undefined) {userId = ""}
            	console.log ('Passing HiddenPrechatUserId = userId (currently Logged In User Id, or ' + userId + ')');
                sessionStorage.setItem("userId", userId);
             // Send it!
             	embeddedservice_bootstrap.prechatAPI.setHiddenPrechatFields({'userId' : userId});
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
             callPrechatAPI();
            });
            window.addEventListener ("load", trapButtonClick);
        </script>
    </body>
</html>
