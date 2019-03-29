# Data Access Layer Basics

- The DAL class will inherit from Entity Framework's DbContext class in order to get all the functionallity to map our 
entity classes to the database tables.
- You can think of this class as being a virtual representation of the database

```C#
using System;
using System.Collections.Generic;
using System.Data.Entity; // DbContext is in this namespace
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using WestWindModels;

namespace WestWindSystem.DAL
{
    // Our DAL class will inherit from EF's DbContext class
    // in order to get all the functionallity to map our
    // Entity classes to the database tables
    // You can think of this context class as being a 
    // virtual representation of the database.
    internal class WestWindContext : DbContext
    {
        #region Constructors
        public WestWindContext() : base("name=WWdb")
        {
            // We can programmatically prevent the default behavior 
            // that EF uses, which is to create the database if it 
            // can't find it based on the connection string name above.
            Database.SetInitializer<WestWindContext>(null); // Prevent initialization
        }
        #endregion

        #region Properties
        public DbSet<Product> Products { get; set; }
        public DbSet<Supplier> Suppliers { get; set; }
        public DbSet<Category> Categories { get; set; }
        #endregion
    }
}
```
