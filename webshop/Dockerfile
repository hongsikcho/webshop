# 기본 .NET SDK 이미지 사용 (빌드 단계)
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# 프로젝트 파일 복사 및 복원
COPY *.sln ./
COPY webshop/*.csproj webshop/
RUN dotnet restore webshop/webshop.csproj

# 프로젝트 빌드
COPY webshop/. webshop/
RUN dotnet publish webshop/webshop.csproj -c Release -o /publish

# 런타임 환경 설정
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /publish .
ENTRYPOINT ["dotnet", "webshop.dll"]
