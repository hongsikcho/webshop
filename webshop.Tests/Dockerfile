FROM mcr.microsoft.com/dotnet/sdk:8.0 AS test
WORKDIR /app

COPY *.sln ./
COPY webshop/*.csproj webshop/
COPY webshop.Tests/*.csproj webshop.Tests/
RUN dotnet restore webshop.Tests/webshop.Tests.csproj

COPY webshop/. webshop/
COPY webshop.Tests/. webshop.Tests/
WORKDIR /app/webshop.Tests
ENTRYPOINT ["dotnet", "test"]
