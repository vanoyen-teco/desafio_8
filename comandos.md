# Entregable Nº 8
## Alumno: Juan Manuel Rodriguez Van Oyen

Creando un usuario Admin:
```
db.createUser({
    user: 'admin',
    pwd: 'admin',
    roles: [{ role: 'dbOwner', db:'ecommerce'}]
});
```

Creando un usuario Lector: 
db.createUser(
  {
    user: "pepe",
    pwd: "asd456",
    roles: [
       { role: "read", db: "ecommerce" }
    ]
  }
)

Crear una coleccion:
db.createCollection("productos")
db.createCollection("mensajes")

Agregar Mensajes:
db.mensajes.insertOne({ user: "juan@juan.com", message: "Hola!", time: new Date() })
db.mensajes.insertOne({ user: "juan@juan.com", message: "Mensaje Nº 1", time: new Date() })
db.mensajes.insertOne({ user: "juan@juan.com", message: "Mensaje Nº 2", time: new Date() })
db.mensajes.insertOne({ user: "juan@juan.com", message: "Mensaje Nº 3", time: new Date() })
db.mensajes.insertOne({ user: "juan@juan.com", message: "Mensaje Nº 4", time: new Date() })
db.mensajes.insertOne({ user: "juan@juan.com", message: "Mensaje Nº 5", time: new Date() })
db.mensajes.insertOne({ user: "juan@juan.com", message: "Mensaje Nº 6", time: new Date() })
db.mensajes.insertOne({ user: "juan@juan.com", message: "Mensaje Nº 7", time: new Date() })
db.mensajes.insertOne({ user: "juan@juan.com", message: "Mensaje Nº 8", time: new Date() })
db.mensajes.insertOne({ user: "juan@juan.com", message: "Mensaje Nº 9", time: new Date() })

Agregar Productos:
db.productos.insertOne({ titulo: "Finder", precio: 120, thumbnail: "https://cdn3.iconfinder.com/data/icons/logos-brands-3/24/logo_brand_brands_logos_finder-128.png" })
db.productos.insertOne({ titulo: "Illustrator", precio: 580, thumbnail: "https://cdn3.iconfinder.com/data/icons/logos-brands-3/24/logo_brand_brands_logos_adobe_illustrator-128.png" })
db.productos.insertOne({ titulo: "Sketch", precio: 900, thumbnail: "https://cdn3.iconfinder.com/data/icons/logos-brands-3/24/logo_brand_brands_logos_sketch_app-128.png" })
db.productos.insertOne({ titulo: "Google", precio: 1280, thumbnail: "https://cdn3.iconfinder.com/data/icons/logos-brands-3/24/logo_brand_brands_logos_google-128.png" })
db.productos.insertOne({ titulo: "Android", precio: 1700, thumbnail: "https://cdn3.iconfinder.com/data/icons/logos-brands-3/24/logo_brand_brands_logos_android-128.png" })
db.productos.insertOne({ titulo: "iCloud", precio: 2300, thumbnail: "https://cdn3.iconfinder.com/data/icons/logos-brands-3/24/logo_brand_brands_logos_icloud-128.png" })
db.productos.insertOne({ titulo: "Paypal", precio: 2860, thumbnail: "https://cdn3.iconfinder.com/data/icons/logos-brands-3/24/logo_brand_brands_logos_paypal-128.png" })
db.productos.insertOne({ titulo: "Skrill", precio: 3350, thumbnail: "https://cdn3.iconfinder.com/data/icons/logos-brands-3/24/logo_brand_brands_logos_skrill-128.png" })
db.productos.insertOne({ titulo: "Adobe", precio: 4320, thumbnail: "https://cdn3.iconfinder.com/data/icons/logos-brands-3/24/logo_brand_brands_logos_adobe-128.png" })
db.productos.insertOne({ titulo: "Firefox", precio: 4990, thumbnail: "https://cdn3.iconfinder.com/data/icons/logos-brands-3/24/logo_brand_brands_logos_firefox-128.png" })

Listar todos los documentos:
db.productos.find()
db.mensajes.find()

Contar todos los documentos:
db.mensajes.countDocuments()
db.productos.countDocuments()

Crear un producto mas a la colección: 
db.productos.insertOne({ titulo: "Commander", precio: 6000, thumbnail: "https://cdn3.iconfinder.com/data/icons/logos-brands-3/24/logo_brand_brands_logos_total_commander-128.png" })

Listar un producto con nombre:
db.productos.find( { titulo: "iCloud" } )

Listar los productos con precio menor a 1000
db.productos.find( { precio: { $lt: 1000 } } )

Listar los productos con precio entre 1000 y 3000
db.productos.find({ precio: { $gt: 1000, $lt: 3000} })

Listar los productos con precio mayor a 3000
db.productos.find( { precio: { $gt: 3000 } } )

Realiza una consulta que traiga sólo el nombre del tercer producto más barato
db.productos.find( {}, { titulo: 1, _id: 0 } ).sort( { precio: 1 } ).skip(2).limit(1)

Actualizar todos los productos agregando un campo "stock" con un valor de 100
db.productos.updateMany({},{ $set: {stock: 100} },false,true)

Cambiar el stock a 0 de todos los productos con precio mayor a 4000
db.productos.updateMany({ precio: { $gt: 4000 } },{ $set: {stock: 0} },false,true)

Eliminar los productos con precio menor a 1000
db.productos.deleteMany({ precio: { $lt: 1000 } })

Loguearse como usuario específico
db.auth('pepe', 'asd456')