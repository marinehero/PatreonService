FROM microsoft/aspnetcore-build:2.0.6-2.1.104 AS builder
WORKDIR /source

COPY *.csproj .
RUN dotnet restore

COPY . .
RUN dotnet publish --output /app/ --configuration Release

FROM microsoft/aspnetcore:2.0.6
WORKDIR /app
COPY --from=builder /app .
ENTRYPOINT ["dotnet", "PatreonService.dll"]