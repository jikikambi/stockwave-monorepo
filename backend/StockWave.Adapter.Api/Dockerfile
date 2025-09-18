# Stage 1: Build
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src

# Copy the csproj for restore (context is already backend/StockWave.Adapter.Api)
COPY *.csproj ./
RUN dotnet restore "StockWave.Adapter.Api.csproj"

# Copy the rest of the files
COPY . .
WORKDIR /src
RUN dotnet publish "StockWave.Adapter.Api.csproj" -c Release -o /app/publish /p:UseAppHost=false

# Stage 2: Runtime
FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .
EXPOSE 5000
ENV ASPNETCORE_URLS=http://+:5000
ENTRYPOINT ["dotnet", "StockWave.Adapter.Api.dll"]
