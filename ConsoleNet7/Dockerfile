FROM mcr.microsoft.com/dotnet/sdk:7.0-alpine3.18 as build
WORKDIR /app
COPY . .
RUN dotnet restore && dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/runtime:7.0-alpine3.18 as runtime
COPY --from=build /app/publish /app/publish
WORKDIR /app/publish
CMD ["dotnet", "ConsoleNet7.dll"]