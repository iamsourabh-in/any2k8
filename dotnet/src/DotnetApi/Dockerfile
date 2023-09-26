# Use a Linux-based .NET 7 runtime image
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
WORKDIR /app
EXPOSE 80

# Use a Linux-based .NET 7 SDK image for building
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY ["DotnetApi.csproj", "DotnetApi/"]
RUN dotnet restore "DotnetApi/DotnetApi.csproj"
WORKDIR "/src/DotnetApi"
COPY . .
RUN dotnet build "DotnetApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "DotnetApi.csproj" -c Release -o /app/publish

# Use the base image for the final runtime
FROM base AS final
ENV COMPlus_EnableDiagnostics=0
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["./DotnetApi"]
