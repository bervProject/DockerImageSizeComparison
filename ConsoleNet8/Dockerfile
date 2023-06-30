FROM mcr.microsoft.com/dotnet/sdk:8.0-preview-alpine3.18 as build
WORKDIR /app
COPY . .
RUN dotnet restore && dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/runtime:8.0-preview-alpine3.18 as runtime
COPY --from=build /app/publish /app/publish
WORKDIR /app/publish
CMD ["dotnet", "ConsoleNet8.dll"]