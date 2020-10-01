*** Docker setup ****

To create a network:

```
docker network create my_network
```

Pull a SQL Server 2019 image:
```
docker pull  mcr.microsoft.com/mssql/server:2017-latest-ubuntu
```

To run SQL Server 2017 for Ubuntu image in a container and add it to our network:

```
docker run  -e ACCEPT_EULA=Y -e SA_PASSWORD=yourStrongPassword12#$ -e 'MSSQL_PID=Express' -p 1433:1433 -v sqldata:/var/opt/mssql --rm --network my_network --name sqlserver -d  mcr.microsoft.com/mssql/server:2017-latest-ubuntu
```

To inspect the network:
```
docker network inspect my_network
```

Build our web app image:
```
docker build -f "./MyDataSite/Dockerfile" -t iiva/asp-data-app .
```

Add our web app to the network:
```
docker run -p 5000:90 --rm --name web_app --network my_network iiva/asp-data-dev
```

Using `docker-compose`:
```
docker-compose build
docker-compose up
```

Go to [http://localhost:5000](http://localhost:5000)
