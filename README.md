# Summary

This project contains two simple modifications to .NET Entity Framework Core's default templates for generating DbContexts and EntityTypes. These changes are to do the following:

- Provide the entity-specific configuration in a new class per entity, which takes the name `<EntityType>Configuration`
- Automatically call all of these entity-specific configurations in the `OnConfiguring` method for the `DbContext` rather this configuration being found here

# Usage

In order to use these templates you first need to install the templates package for EF Core in your project:

```bash
dotnet new install Microsoft.EntityFrameworkCore.Templates
```

After this, you can copy the two `t4` files from this project into your `CodeTemplates/EFCore` folder in the root of your project. If you are unsure of where these should be placed, you can generate the default versions from EF Core and then overwrite them with these versions. To do this, run the command:

```bash
dotnet new ef-templates
```

Once the templates are in place, you can scaffold your files as you usaually would with EF Core. For example, to scaffold a new DbContext and EntityTypes for a database called `MyDatabase` on `localhost` using the `Microsoft.EntityFrameworkCore.SqlServer` database provider, you could run the command:

```bash
dotnet ef dbcontext scaffold "Server=localhost;Initial Catalog=MyDatabase;TrustServerCertificate=True" Microsoft.EntityFrameworkCore.SqlServer
```
