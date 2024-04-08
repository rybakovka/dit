FROM mcr.microsoft.com/dotnet/sdk:6.0-jammy as build
WORKDIR /src
COPY . /src
RUN dotnet restore ./WebApplication_DIT_Docker/WebApplication_DIT_Docker.csproj 
RUN dotnet build ./WebApplication_DIT_Docker/WebApplication_DIT_Docker.csproj --no-restore --configuration Release
RUN dotnet publish ./WebApplication_DIT_Docker/WebApplication_DIT_Docker.csproj --no-build --configuration Release -o /src/publish

FROM mcr.microsoft.com/dotnet/aspnet:6.0-jammy 
WORKDIR /app
COPY --from=build /src/publish ./
EXPOSE 80
ENTRYPOINT [ "dotnet", "WebApplication_DIT_Docker.dll" ]
