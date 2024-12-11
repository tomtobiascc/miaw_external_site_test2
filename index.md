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
        onload='initEmbeddedMessaging()'>
        </script>

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
                identityTokenType: "JWT", identityToken: "eyJraWQiOiIxMjM0NSIsImFsZyI6IlJTMjU2In0.eyJpc3MiOiJ0ZXN0SXNzdWVyIiwic3ViIjoidXNlcjIiLCJleHAiOjE3MzQ0NzQ5NzUsImlhdCI6MTczMzg3NDk3NX0.do9fZe6UJhs3KCkqQ98ss5A70JkRpNr-l7Gl1PsuKNN0zL0_TzEaaC6wkyhlOYW94JHLAhfrthfNsJT94kDsAIMbcdaFxk8Dt4a9ewI6sYHk6LpnVoQo53QUzPoKI7m8iwahls461uH60JoiGmHXIPgWOa4XuHEd3Ufp0qIa9uHlogiI00nCJSADxPPIDL0Pt121PYAwH0r5l8rf9hEQuUxkxri8MbRsKPeND8yCld4CXLKSXtrrO_6ULA9fCx52ipL4BOx6wB6uhz1Jz26AKiBikUTwAq6pnpG3L9onGAiZaM16kM3iE0VCAy_seEQDNhGk22DatLry7toCY1hx5Q"
            });
            console.log('Sent JWT');
            // pass the userId into our prechat lwc
            embeddedservice_bootstrap.prechatAPI.setVisiblePrechatFields({
                "userId": {
                    "value": "005V9000004u9kfIAA",
                    "isEditableByEndUser": false
                }
            });
        });
        window.addEventListener("load", trapButtonClick);
    </script>
</body>

</html>
