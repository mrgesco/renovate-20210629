
**Current**

When renovate parses the composer file and tries to check the version, it gives a 404 error while trying to check on packagist instead of the right repository url.

    https://packagist.org/p/***REDACTED***.json

**Expected**

As instanciated in composer.json

    https://<GITLAB_URL>/......json

**Debug**

    DEBUG: packageFiles with updates (repository=***REDACTED***)
	"config": {
	    "composer": [
	    {
	        "packageFile": "composer.json",
	        "deps": [
	        ......
	        {
	            "depType": "require",
	            "depName": "***REDACTED***",
	            "currentValue": "^3.0",
	            "datasource": "packagist",
	            "lockedVersion": "3.0.0",
	            "depIndex": 18,
	            "updates": [],
	            "warnings": [
	            {
	                "topic": "***REDACTED***",
	                "message": "Failed to look up dependency ***REDACTED***"
	            }
	            ]
	        }
	        ],
	        "lockFiles": ["composer.lock"],
	        "registryUrls": [
	           "https://wpackagist.org",
	           "https://<GITLAB_URL>/api/v4/group/<GOURP_ID>/-/packages/composer",
	           "https://packagist.org"
	        ],
	    }
	...
	DEBUG: exec completed (repository=***REDACTED***, branch=renovate/lock-file-maintenance)
	       "cmd": "composer update --with-dependencies --ignore-platform-reqs --no-ansi --no-interaction --no-scripts --no-autoloader",
	       "durationMs": 6604,
	       "stdout": "",
	       "stderr": "Loading composer repositories with package information\nUpdating dependencies\nLock file operations: 0 installs, 1 update, 0 removals\n- Installing ***REDACTED***/***REDACTED*** (3.0.0):
