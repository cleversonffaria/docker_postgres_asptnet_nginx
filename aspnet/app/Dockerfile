FROM mcr.microsoft.com/dotnet/core/aspnet AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/core/sdk AS build
WORKDIR /src
COPY ["NOME_DA_PASTA/NOME_DO_ARQUIVO.csproj",""]
RUN dotnet restore "./NOME_DO_ARQUIVO.csproj"
COPY . .
WORKDIR /src
RUN dotnet build "NOME_DA_PASTA/NOME_DO_ARQUIVO.csproj" -c Release -o /NOME_DA_PASTA/build

FROM build AS publish
RUN dotnet publish "NOME_DA_PASTA/NOME_DO_ARQUIVO.csproj" -c Release -o /NOME_DA_PASTA/publish

RUN dotnet --version

FROM base AS final
WORKDIR /app
COPY --from=publish /NOME_DA_PASTA/publish .

ENV ASPNETCORE_URLS http://*:5000
EXPOSE 5000
ENTRYPOINT [ "dotnet","NOME_DO_ARQUIVO.csproj","--server.urls","HTTP://*:5000" ]
