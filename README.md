# AccountActivity
 Implementation of Account Activity API for Tweepy, this is to address https://github.com/tweepy/tweepy/issues/1075
 
 Twitter changed its delivery of events on user accounts to a single application hook with the Account Activity API. This API is documented at https://developer.twitter.com/en/docs/accounts-and-users/subscribe-account-activity/api-reference/aaa-premium
 
 This documentation is largely accurate though there are some minor errors. The endpoints are all expressed as path URLs but in the detail most of them are a URL to a JSON file. That JSON file is the response and not the request, even when the request is a POST or PUT. 
 
 *Aside* Whether this is why binder_api() requires a parameter reference (even if there is no parameter) in order to execute rather than return the model is unknown but forming the bind_api() calls like this works. There may well be a tidier way of forming these calls if it was ever merged into tweepy itself.
 
 The API generally requires User access authentication (OAuth1) but there are some general calls which only require a bearer token (OAuth2) GET account_activity/all/webhooks or GET account_activity/all/:env/webhooks
 
 The env string is the environment defined for the application and is necessary for any sandbox application. Only Enterprise applications have a production environment. The ':' is not part of the URL path.
 
 
 
 **TODO**
 
 PUT account_activity/all/:env_name/webhooks/:webhook_id.json
 DELETE account_activity/all/:env_name/webhooks/:webhook_id.json
 DELETE account_activity/all/:env_name/subscriptions/:user_id.json
 
