FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /Estudos-Docker-Net-Core
COPY ["Estudos-Docker-Net-Core.csproj", "./"]
RUN dotnet restore "Estudos-Docker-Net-Core.csproj"
COPY . .
WORKDIR /Estudos-Docker-Net-Core
RUN dotnet build "Estudos-Docker-Net-Core.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "Estudos-Docker-Net-Core.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "Estudos-Docker-Net-Core.dll"]
