# escape=`
FROM microsoft/nanoserver
ENV CADDY_VERSION 0.10.5
RUN mkdir C:\caddy\conf
RUN mkdir C:\wwwroot

RUN powershell -Command $ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue'; `
    if ($env:HTTP_PROXY) {$global:PSDefaultParameterValues=@{'Invoke-WebRequest:Proxy'=$env:HTTP_PROXY;'Invoke-WebRequest:ProxyUseDefaultCredentials'=$true}}; `
    Invoke-WebRequest $('https://github.com/mholt/caddy/releases/download/v{0}/caddy_v{0}_windows_amd64.zip' -f $env:CADDY_VERSION) -OutFile 'caddy.zip' -UseBasicParsing; `
    Expand-Archive -Path caddy.zip -DestinationPath C:\caddy -Force ; `
    rm caddy.zip

WORKDIR C:\caddy

EXPOSE 80

# COPY CONTENT INTO Container
COPY ./conf C:/caddy/conf
COPY ./www C:/wwwroot

ENTRYPOINT [ "C:\\caddy\\caddy.exe" ]

CMD [ "-conf", "C:\\caddy\\conf\\Caddyfile" ]
