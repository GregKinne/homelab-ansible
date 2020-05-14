# Build arm64 cloudfared binary

## Download, unpack,configure go
curl https://dl.google.com/go/go1.13.3.linux-amd64.tar.gz >> /tmp/go1.13.3.linux-amd64.tar.gz

tar -xvf /tmp/go1.13.3.linux-amd64.tar.gz
sudo mv go /usr/local

export GOROOT=/usr/local/go
export GOPATH=$HOME
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH


## Get the source
go get -v github.com/cloudflare/cloudflared/cmd/cloudflared

## Build for arm64
GOOS=linux GOARCH=arm64 go build -v -x github.com/cloudflare/cloudflared/cmd/cloudflared

#3 Copy to Raspberry Pi
scp cloudflared <user>@<host>:<destination>


