FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /DockerSource

# Copy everything else and build
COPY ./JenkinsExample .
WORKDIR /DockerSource
RUN dotnet restore
RUN dotnet publish -c release -o /Output --no-restore

# Final stage / image
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /App
COPY --from=build /Output .

EXPOSE 80
ENTRYPOINT ["dotnet", "JenkinsExample.dll"]
