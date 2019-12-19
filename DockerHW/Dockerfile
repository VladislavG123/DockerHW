

FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-buster-slim AS base
WORKDIR /app
EXPOSE 80
FROM mcr.microsoft.com/dotnet/core/sdk:3.0-buster AS build
WORKDIR /src
COPY ["DockerHW.csproj", "DockerHW1/"]
RUN dotnet restore "DockerHW1/DockerHW.csproj"
COPY . .
RUN dotnet build "DockerHW.csproj" -c Release -o /app/build
FROM build AS publish
RUN dotnet publish "DockerHW.csproj" -c Release -o /app/publish
FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "DockerTestLesson.dll"]