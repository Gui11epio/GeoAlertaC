# Etapa base
FROM mcr.microsoft.com/dotnet/aspnet:8.0-alpine AS base
WORKDIR /app
EXPOSE 8080
EXPOSE 8081

# Etapa de build
FROM mcr.microsoft.com/dotnet/sdk:8.0-alpine AS build
ARG BUILD_CONFIGURATION=Release
WORKDIR /src
COPY GeoAlertaC/GeoAlertaC.csproj GeoAlertaC/
RUN dotnet restore "GeoAlertaC/GeoAlertaC.csproj"
COPY GeoAlertaC/ GeoAlertaC/
WORKDIR /src/GeoAlertaC
RUN dotnet build "GeoAlertaC.csproj" -c $BUILD_CONFIGURATION -o /app/build

# Etapa de publicação
FROM build AS publish
ARG BUILD_CONFIGURATION=Release
RUN dotnet publish "GeoAlertaC.csproj" -c $BUILD_CONFIGURATION -o /app/publish /p:UseAppHost=false

# Etapa final
FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "GeoAlertaC.dll"]
