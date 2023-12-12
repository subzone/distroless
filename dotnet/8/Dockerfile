# Stage 1: Build the application
FROM microsoft/dotnet:8-sdk AS build-env

# Copy your application files to /app
WORKDIR /app
COPY . .

# Restore NuGet dependencies
RUN dotnet restore

# Build the application in release mode
RUN dotnet build -c Release

# Stage 2: Create the final image
FROM gcr.io/distroless/dotnet:8

# Copy the published application
COPY --from=build-env /app/bin/Release/net8.0/publish /app

# Set the entrypoint to run the application
ENTRYPOINT ["dotnet", "MyApplication.dll"]