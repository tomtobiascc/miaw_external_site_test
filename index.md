<html>

<body>
    <script type='text/javascript'>
        // code snippet created by the Embedded Service Deploying page after being configured
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
    <script type='text/javascript'
        src='https://billcom--messaging.sandbox.my.site.com/ESWMessagingforVerified1730416007264/assets/js/bootstrap.min.js'
        onload='initEmbeddedMessaging()'></script>

    <script>
        function trapButtonClick() {
            console.log('Looking for embeddedMessagingConversationButton...');
            var b = document.getElementById('embeddedMessagingConversationButton');
            if (b != null) {
                console.log('Found it, attaching to onClick event');

            } else {
                console.log('No button yet; wait a second and try again');
                setTimeout(trapButtonClick, 1000);
            }
        }
        window.addEventListener("onEmbeddedMessagingReady", () => {
            console.log('Received the onEmbeddedMessagingReady event...');
            // sending JWT allows messaging button to appear if approved
            embeddedservice_bootstrap.userVerificationAPI.setIdentityToken({
                identityTokenType: "JWT", identityToken: "eyJraWQiOiIxMjM0NSIsImFsZyI6IlJTMjU2In0.eyJpc3MiOiJ0ZXN0SXNzdWVyIiwic3ViIjoidXNlcjEiLCJleHAiOjE3NDA1NDA3MDYsImlhdCI6MTczNDU0MDcwNn0.XvIGH8pfDMK_DJKrWcjykmaVZrQDc4FuhnSOO4TYcxtbeqD4UI43hW7XLXAqwb8p7TCbde1sNw0aQ8pLnviUvhNkCtOALE3WNilJsA5x-VqsE4SnRmo36sdJTh7kbH16mU5EH5Hsj8z7gOoJvyuQ1aQHWA0W94AvYjPHh6iyNlW4xZK-z4PPLkFOtGf3Vjyry5Pew03NZCGhpqmaeDiORmXrBO22Q2-kfgDxDFaZhGzPQu9ufm5HnftbASjNf2ambYgTgIk9LJY__bjOhtuWJIkSvd_T4-kDr4GdRezIqS6rLE-kCxpaS-bR6xYpLld32mqs6uElNcyT6c1NWr0-oA"
            });
            console.log('Sent token');
            // pass the userId into our prechat lwc
            embeddedservice_bootstrap.prechatAPI.setVisiblePrechatFields({
                "userId": {
                    "value": "005V9000004FWy3IAG",
                    "isEditableByEndUser": false
                }
            });
        });
        window.addEventListener("load", trapButtonClick);
    </script>
</body>

</html>
