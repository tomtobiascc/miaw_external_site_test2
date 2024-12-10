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
    identityTokenType: "JWT", identityToken: "eyJraWQiOiIxMjM0NSIsImFsZyI6IlJTMjU2In0.eyJpc3MiOiJ0ZXN0SXNzdWVyIiwic3ViIjoidXNlcjIiLCJleHAiOjE3MzQzODk0ODcsImlhdCI6MTczMzc4OTQ4N30.SI4hgsnWUK_yETE9jiNeAlfwkCTMnJn4MTUckqL45QYY7JfpvDvY8DUC2Am3A9aP-db1WnpVBQZXy_YbGJFwvIQEmiZuiV3fBbyMCUNGQEJPr5FNamYlqesM-SrpkkxMWOcynQ5ZIbmvEnCCAsw_tQm25Q_n-fnkQOQv7QA7nnIolcxgv7gI5dToXL29R97rKnYK8AAYq0i-2FC-Z9hlxYppXmgTiLWVdZMXm9ZxoDYu3DqnpxaRAxQSicuKBW8voicqnQTCxDDP1sC8KGBpfZES8V9D-8h08khBlQ3iPPh6LLU_ZhmXVVvUw4kB0SuY8PLhcRMUfiSkBl5qUoFWpw"});
    

            embeddedservice_bootstrap.prechatAPI.setVisiblePrechatFields({
                "userId": {
                    "value": "005V9000004u9kfIAA",
                    "isEditableByEndUser": false
                }
            });
             callPrechatAPI();
            });
            window.addEventListener ("load", trapButtonClick);
        </script>
    </body>
</html>
