FROM mcr.microsoft.com/dotnet/sdk:6.0-alpine3.18 as build
WORKDIR /app
COPY . .
RUN dotnet restore && dotnet publish -c Release -o /app/publish && chmod +x "/app/publish/SingleConsoleNet6"

FROM alpine:3.18 as runtime
COPY --from=build /app/publish /app/publish
WORKDIR /app/publish
# install required lib
RUN apk upgrade --no-cache && apk add --no-cache libgcc libstdc++
CMD ["./SingleConsoleNet6"]