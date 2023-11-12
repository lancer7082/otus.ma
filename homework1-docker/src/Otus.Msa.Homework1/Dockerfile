FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 8000

ENV ASPNETCORE_URLS=http://+:8000

# Creates a non-root user with an explicit UID and adds permission to access the /app folder
# For more info, please refer to https://aka.ms/vscode-docker-dotnet-configure-containers
RUN adduser -u 5678 --disabled-password --gecos "" appuser && chown -R appuser /app
USER appuser

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
ARG configuration=Release
WORKDIR /src
COPY ["./../Otus.Msa.Homework1.csproj", "Otus.Msa.Homework1/"]
RUN dotnet restore "Otus.Msa.Homework1/Otus.Msa.Homework1.csproj"
COPY . "Otus.Msa.Homework1/"
WORKDIR "Otus.Msa.Homework1"
RUN dotnet build "Otus.Msa.Homework1.csproj" -c $configuration -o /app/build

FROM build AS publish
ARG configuration=Release
RUN dotnet publish "Otus.Msa.Homework1.csproj" -c $configuration -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Otus.Msa.Homework1.dll"]
