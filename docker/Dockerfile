# >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
# DO NOT EDIT THIS FILE. IT IS AUTO_GENERATED
# >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
FROM cyberdojofoundation/csharp:4586a83

# >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
# START of extra commands to fulfil runner's requirements (os=Alpine)
RUN (getent group sandbox) || (addgroup -g 51966 sandbox)
RUN (grep -q sandbox:x:41966 /etc/passwd) || (adduser -D -g "" -h /home/sandbox -G sandbox -s /bin/bash -u 41966 sandbox)
RUN apk add --update coreutils bash tar file
ARG GIT_COMMIT_SHA
ENV SHA=${GIT_COMMIT_SHA}
# END of extra commands to fulfil runner's requirements
# >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

LABEL maintainer=jon@jaggersoft.com

COPY packages.config .

RUN \
apk add --update openssl && \
wget http://dist.nuget.org/win-x86-commandline/latest/nuget.exe && \
mono --runtime=v4.5 nuget.exe restore -PackagesDirectory . && \
mkdir /nunit && \
mv NUnit.*/lib                  /nunit && \
mv NUnit.ConsoleRunner.*/tools  /nunit

COPY red_amber_green.rb /usr/local/bin
