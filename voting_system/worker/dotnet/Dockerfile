FROM mcr.microsoft.com/dotnet/core/sdk:2.1 AS builder

WORKDIR /Worker
COPY Worker/Worker.csproj .
RUN dotnet restore

COPY /Worker .
RUN dotnet publish -c Release -o /out Worker.csproj

# app image
FROM mcr.microsoft.com/dotnet/core/aspnet:2.1

WORKDIR /app
ENTRYPOINT ["dotnet", "Worker.dll"]

COPY --from=builder /out .