# Steps to build

### Pre-requisites
> Make sure you have the following packages cloned and zimbra setup to run the zimlet.

`$> git clone ssh://git@stash.corp.synacor.com:7999/zimbra/zm-zcs.git ../zm-zcs`

`$> git clone https://github.com/Zimbra/zimbra-package-stub.git ../zimbra-package-stub`

### To deploy com\_zimbra\viewmail zimlet
1). `$> mkdir ~/.zcs-deps`

2). Ensure that the following jar is present under `~/.zcs-deps` dir.

> ant-contrib-1.0b1.jar (or you may install ant-contrib globally).

	The following dependencies would be resolved automatically:
	
	* commons-codec
	* commons-httpclient
	* com.google.guava
	* javax.mail
	* dom4j
	* log4j
	* com.unboundid

	The following need to be published individually using ant publish-local.
	* zm-client
	* zm-common
	* zm-soap
	* zm-store
	* zm-native

3.) `$> ant package-zimlet` or `$> ant deploy-zimlet` - Deploys the zimlet.

4.) `$> ant undeploy-zimlet` - Undeploys the zimlet.

Note: You might need to run `$> zmmailboxdctl restart` after deploying and undeploying the zimlet.