<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Github Messaing Page</title>
        <meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1">
    </head>
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
                onload='initEmbeddedMessaging()'></script>
    </body>
</html>
