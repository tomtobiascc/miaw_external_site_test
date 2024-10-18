<html>
    <body>
        <script type='text/javascript'>
            sessionStorage.setItem("userId", "005V9000004FWy3IAG");
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
