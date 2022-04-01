<h1 style="color:yellow">
 Data Sources
</h1>
They are like a Glue for multiple configurations and we have to say Resources are data sources too. 
Providers also have data source too, for example when you want to use one of the AMIs from the AWS. you can use data source to get the coresponding information for that.

<h2 style="color:yellow">
 best part (Alternate data source)
</h2>
you can use these Alternate data sources:

- Template 
- HTTP
- External
- Consul 


<h2 style="color:yellowgreen">
HTTP Data Source
</h2>

to use HTTP Data source, you just need to use code below
```
data "http" "my_ip" {
    url = "http://ifconfig.me"
}
```

### Using the response 
```
data.http.my_ip.body
```

<h2 style="color:yellowgreen">
Consul Data Source
</h2>

to use Consul Data source, you just need to use code below
```
data "consul_keys" "networking" {
    key {
        name = "vpc_cidr_range"
        path = "networking/config/vpc/cidr_range"
        default = "10.0.0.0/16"
    }
}
```

### Using the response 
```
data.consul_keys.networking.var.vpc_cidr_range
```