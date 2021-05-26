# Thousandeyes Terraform Pageload Module
 
This module allows for pageload testing with ThousandEyes through the Terraform platform.

This code shows an example of a URL pageload test:

```terraform
resource "thousandeyes_page_load" "test2" {
  test_name = "website_pageload"
  
  alerts_enabled         = 0
  bandwidth_measurements = 0
  network_measurements   = 0

  content_regex = ".*"
  
  url      = var.test_page
  
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

The required variables are the ThousandEyes OAuth Bearer Token which can be found under ```Account Settings>User and Roles>User API Tokens``` in the ThousandEyes dashboard and the link of the page the test should be perfomed on.

```terraform
variable "te_token" {
  type    = string
  description = "thousandEyes dashboard API token"
}

variable "test_page" {
  type    = string
  description = "website of the page that the test will be perfomed on"
}
```
After running the pageload test, the test result should show up in your ThousandEyes dashboard.
