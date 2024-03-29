# DrinkApp

  

DrinkApp es una aplicación de compra de bebidas con y sin alcohol.

  

## Funcionalidades

### Productos

  

Para efectuar la compra de un producto, la aplicación cuenta con las siguientes funcionalidades:

  

### Casos de uso

 **Agregar producto**

Endpoint:  `/api/product`

Método: addProduct(product) - **POST**

Para agregar un producto se tendrá que enviar un json con este cuerpo: 

     {
    
	    "name":"", //nombre del producto
	    
	    "price":, //precio unitario
	    
	    "description":"", // descripción del producto
	    
	    "brand":"", // marca del producto
	    
	    "category":"", // categoría del producto

	    "stock":, // cantidad stock

            "image":"", // imagen del producto
	    
	    "alcohol": true / false //tiene alcohol
    
    }
Se agregará a nuestra base de datos MongoDB en la colección *products*.

  

---
  


**Obtener productos**

Endpoint: `/api/products`

Método: getProducts() - **GET**

Utilizando el get en nuestro endpoint nuestra api devolverá en formato json todos los productos almacenados en nuestra base de datos.

---

  

**Modificar productos**


Endpoint: `/api/products/:idProducto`

Método: updateProduct(product) - **PUT**

Se tendrá que saber el id del producto para modificarlo y completar el json de la misma manera que en el caso de agregar el producto. Al completar y enviar el request habrá una respuesta positiva (status 200) donde nos comunicará el que producto ha sido modificado o una respuesta negativa (status 404) comuniucando que el producto no ha sido encontrado.

---
**Eliminar producto**


Endpoint: `/api/products/:idProducto`

Método: deleteProduct(idProducto) - **DELETE**

Para eliminar un producto se tendrá que hacer un request a nuestra api con este endpoint, sabiendo el id del producto a eliminar.
Recibiremos una respuesta positiva (status 200) comunicando que el producto ha sido eliminado o una respuesta negativa (status 404) en caso de no haber encontrado un producto con el id solicitado.

---
**Eliminar producto**


Endpoint: `/api/products/:idProducto`

Método: deleteProduct(idProducto) - **DELETE**

Para eliminar un producto se tendrá que hacer un request a nuestra api con este endpoint, sabiendo el id del producto a eliminar.
Recibiremos una respuesta positiva (status 200) comunicando que el producto ha sido eliminado o una respuesta negativa (status 404) en caso de no haber encontrado un producto con el id solicitado.

---
**Producto con el precio más alto**


Endpoint: `/api/products/expensive`

Método: getProducts() - **GET**

Para saber cuál bebida tiene el precio más caro. Mostrará el nombre de la bebida, el precio y su categoría.

---
**Cantidad de bebidas y precio promedio por categoría**


Endpoint: `/api/products/categories`

Método: getCategories() - **GET**

Este get devolverá un json con cada categoría, la cantidad de bebidas con esa categoría y el precio promedio.

--

### Clientes
De la misma manera que en productos, tenemos otra colección en nuestra base de datos destinadas para los clientes con las mismas funcionalidades.

**Agregar cliente**

Endpoint:  `/api/client`

Método: addClient(client) - **POST**

Para agregar un cliente se tendrá que enviar un json con este cuerpo: 

     {
    
	    "fullName":"", // nombre completo del cliente
	    
	    "email":, // email del cliente
	    
	    "phone":, // numero de telefono del cliente
	    
	    "direction":, // direccion del cliente

	    "dateOfBirth":, // fecha de nacimiento del cliente
    
    }
Se agregará a nuestra base de datos MongoDB en la colección *clients*.

  

---
  


**Obtener clientes**

Endpoint: `/api/clients`

Método: getClients() - **GET**

Utilizando el get en nuestro endpoint nuestra api devolverá en formato json todos los clientes almacenados en nuestra base de datos. Por medio de la autenticación que se explicará más adelante.

---
  

**Modificar cliente**


Endpoint: `/api/clients/:idClient`

Método: updateClient(client) - **PUT**

Se tendrá que saber el id del cliente para modificarlo y completar el json de la misma manera que en el caso de agregar el producto. Al completar y enviar el request habrá una respuesta positiva (status 200) donde nos comunicará que el cliente ha sido modificado o una respuesta negativa (status 404) comunicando que el cliente no ha sido encontrado.

---
**Eliminar cliente**
Endpoint: `/api/clients/:idCliente`

Método: deleteClient(idClient) - **DELETE**

Para eliminar un cliente se tendrá que hacer un request a nuestra api con este endpoint, sabiendo el id del cliente a eliminar.
Recibiremos una respuesta positiva (status 200) comunicando que el cliente ha sido eliminado o una respuesta negativa (status 404) en caso de no haber encontrado un cliente con el id solicitado.

---

### Sales

Para realizar el registro de la compra, la aplicación cuenta con las siguientes funcionalidades:
  
### Casos de uso

**Agregar sale**

Endpoint:  `/api/sale`

Método: addSale() - **POST**

Para agregar una venta se tendrá que enviar un json con este cuerpo: 

     {
    
	    "client":"", //nombre del cliente
	    
	    "salesPrice":, //precio total de la compra
	    
	    "payMethod":"", // metodo de pago
	    
	    "products":"", // productos que conforman la compra 
	
    }

Se agregará a nuestra base de datos MongoDB en la colección *sales*.

  
---
  

**Obtener venta**

Endpoint: `/api/:idsale`

Método: getSale(sale) - **GET**

Utilizando el get en nuestro endpoint nuestra api devolverá en formato json la venta seleccionada almacenada en nuestra base de datos.

---

**Obtener ventas**

Endpoint: `/api/sales`

Método: getSales() - **GET**

Utilizando el get en nuestro endpoint nuestra api devolverá en formato json todos las ventas almacenadas en nuestra base de datos.

---
  

**Modificar venta**


Endpoint: `/api/sales/:idSale`

Método: updateSale(sale) - **PUT**

Se tendrá que saber el id de la venta para modificarla y completar el json de la misma manera que en el caso de agregar la venta. 
Al completar y enviar el request habrá una respuesta positiva (status 200) donde nos comunicará que la venta ha sido modificada 
o una respuesta negativa (status 404) comunicando que la venta no ha sido encontrado.

---
**Eliminar venta**


Endpoint: `/api/sales/:idSale`

Método: deleteSale(idsale) - **DELETE**

Para eliminar una venta se tendrá que hacer un request a nuestra api con este endpoint, sabiendo el id de la venta a eliminar.
Recibiremos una respuesta positiva (status 200) comunicando que la venta ha sido eliminada o una respuesta negativa (status 404) 
en caso de no haber encontrado venta con el id solicitado.

--

## Autenticación

Al agregar un cliente en `/api/clients`, para poder acceder a la cuenta, se accede en `/api/clients/login/`, se validará el email y la contraseña. Si un dato es incorrecto devolverá un mensaje comunicando que las credenciales no son válidas, de lo contrario se devolverá el cliente y un token.
 Mediante el token se podrá acceder al `GET` de clients, por medio la implementación del middleware **auth**.
 
 ---

## Licencia

[MIT](https://choosealicense.com/licenses/mit/)
