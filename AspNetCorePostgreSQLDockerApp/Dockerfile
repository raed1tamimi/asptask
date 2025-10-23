FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build

WORKDIR /App


COPY ["AspNetCorePostgreSQLDockerApp.csproj", "./"]
RUN dotnet restore

COPY . .
RUN dotnet publish -o out

FROM mcr.microsoft.com/dotnet/aspnet:3.1
WORKDIR /App

COPY --from=build /App/out .
EXPOSE 80
ENTRYPOINT ["dotnet", "AspNetCorePostgreSQLDockerApp.dll"]
