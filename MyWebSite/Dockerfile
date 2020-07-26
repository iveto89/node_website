FROM mcr.microsoft.com/dotnet/core/sdk:3.1

WORKDIR /app

# copy csproj and restore as distinct layers
COPY MyWebSite.csproj .

COPY . .

EXPOSE 90

CMD dotnet restore && dotnet watch run