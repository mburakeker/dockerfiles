FROM microsoft/nanoserver
ARG VERSION
ENV NOMAD_VERSION $VERSION

RUN powershell -Command $ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue'; \
    Invoke-WebRequest $('https://releases.hashicorp.com/nomad/{0}/nomad_{0}_windows_amd64.zip' -f $env:NOMAD_VERSION) -OutFile 'nomad.zip' -UseBasicParsing ; \
    Expand-Archive -Path nomad.zip -DestinationPath . -Force ; \
    rm nomad.zip ; \
	c:/nomad.exe --version
	
EXPOSE 4646 4647 4648
ENTRYPOINT ["c:/nomad.exe"]
