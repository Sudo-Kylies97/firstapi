FROM microsoft/dotnet:latest AS build-env
WORKDIR /app

# copy csproj and restore as distinct layers
COPY WebApplication1/WebApplication1/*.csproj ./
RUN dotnet restore

# copy everything else and build
COPY  WebApplication1/WebApplication1/. ./
RUN dotnet publish -c Release -o out

# build runtime image
FROM microsoft/dotnet:latest
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "WebApplication1.dll"]
