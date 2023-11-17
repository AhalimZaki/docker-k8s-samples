FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build

WORKDIR /app

COPY *.csproj .

RUN dotnet restore

COPY . .

RUN dotnet publish -c release -o /app

FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base

WORKDIR /app

COPY --from=build /app .
EXPOSE 80
ENTRYPOINT ["dotnet", "sampleapp.dll"]