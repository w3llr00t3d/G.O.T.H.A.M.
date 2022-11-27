# G.O.T.H.A.M.
Getting Other Targets Hackers Always Miss


#AWS
 
#AWS get IPs:

`wget https://ip-ranges.amazonaws.com/ip-ranges.json -O amazon_ips.json`

#get list - one CIDR range per line:

`cat amazon_ips.json | jq -r '[.prefixes[] | select(.service=="EC2").ip_prefix] | .[]' `

#get list - all CIDR ranges on a single comma-ceparated line:

`cat amazon_ips.json | jq -r '[.prefixes[] | select(.service=="EC2").ip_prefix] | .[]' | sed -z 's/\n/,/g;s/,$/\n/'`



# Google Cloud 
#google cloud IPs:

`wget https://www.gstatic.com/ipranges/cloud.json ; cat cloud.json | jq  | grep 'us-west1\|us-west2\|us-central1\|us-east1\|us-east4\|northamerica-northeast1\|us-central2\|us-east5\|us-east7\|us-south1\|us-west3\|us-west4\|asia-east1\|asia-east2\|asia-northeast1\|asia-northeast2\|asia-northeast3\|asia-south1\|asia-south2\|asia-southeast1\|asia-southeast2\|australia-southeast1\|australia-southeast2\|europe-central2\|europe-north1\|europe-southwest1\|europe-west1\|europe-west2\|europe-west3\|europe-west4\|europe-west6\|europe-west8\|europe-west9\|global\|me-west1\|northamerica-northeast2\|southamerica-east1\|southamerica-west1' -B3 | grep ipv4Prefix | cut -d '"' -f4 | awk '{print}' ORS=',' | sed  's/.$//' | sed 's/,/\n/g' >> GC_vog_ips`


Azure:
# Note these links change weekly.

# Public
https://download.microsoft.com/download/7/1/D/71D86715-5596-4529-9B13-DA13A5DE5B63/ServiceTags_Public_20221121.json

# Azure Gov Cloud
https://download.microsoft.com/download/6/4/D/64DB03BF-895B-4173-A8B1-BA4AD5D4DF22/ServiceTags_AzureGovernment_20221121.json
