# Get the base image
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build-env
WORKDIR /app

# Copy the csproj and restore all of the nugets
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out api.csproj

ENV ASPNETCORE_URLS=http://+:5000
EXPOSE 5000

# Build runtime image
FROM mcr.microsoft.com/dotnet/sdk:5.0
WORKDIR /app
COPY --from=build-env /app/out .
# ENTRYPOINT ["dotnet", "api.dll"]
CMD ["dotnet", "run"]