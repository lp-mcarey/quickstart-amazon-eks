# Installing custom EKS quickstart

## Clone

    git clone git@github.com:lp-mcarey/quickstart-amazon-eks.git
    cd quickstart-amazon-eks
    git submodule init
    git submodule update

OR:

    git clone --recurse-submodules git@github.com:lp-mcarey/quickstart-amazon-eks.git

## Deploy

Must be created in us-east-1 or other region that doesn't require AWS4-HMAC-SHA256 which is causing issue for [cfn-init on Bastion autoscale group](https://forums.aws.amazon.com/thread.jspa?threadID=254885).

    aws --region us-east-1 s3 ls s3://aws-quickstart-cm-eng > /dev/null 2>&1 || aws --region us-east-1 s3 mb s3://aws-quickstart-cm-eng --endpoint-url https://s3.us-east-1.amazonaws.com
    aws --region us-east-1 s3 sync . s3://aws-quickstart-cm-eng/quickstart-amazon-eks/ --exclude ".git/*" --exclude ".git*" --exclude "*/.git/*"
