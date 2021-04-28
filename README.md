# Thousandeyes Terraform Pageload Module
 
This module allows for pageload testing with ThousandEyes through the Terraform platform.

This code shows an example of a google.com pageload test:

```terraform
resource "thousandeyes_page_load" "test2" {
  test_name = "google_pageload"
  
  alerts_enabled         = 0
  bandwidth_measurements = 0
  network_measurements   = 0

  content_regex = ".*"
  
  url      = "https://google.com"
  
  interval      = 300
  http_interval = 300
	
  agents {
      agent_id = 144 # Vienna
  }
  
  agents {
      agent_id = 58 # Cairo
  }
  
  agents {
      agent_id = 60411 # Paris (Azure)
  }
	
  agents {
      agent_id = 56289 # Paris (AWS)
  }
	
  agents {
      agent_id = 65163 # Tokyo
  }
}
```

The only required variable is the ThousandEyes OAuth Bearer Token which can be found under ```Account Settings>User and Roles>User API Tokens``` in the ThousandEyes dashboard.

```terraform
variable "te_token" {
  type    = string
  description = "thousandEyes dashboard API token"
}
```
After running the pageload test, the test result should show up in your ThousandEyes dashboard.