Funcion operaciones <- obtenerCambio ( precio, ingreso )
	Dimension monedas[3]
	monedas[1] <- 100
	monedas[2] <- 50
	monedas[3] <- 10
	operaciones <- 0
	
	Repetir
		Para i<-1 Hasta 3 Con Paso 1 Hacer
			Si ingreso >= precio Entonces
				nuevo_ingreso <- ingreso - monedas[i]
				Si nuevo_ingreso >= precio  Entonces
					operaciones <- operaciones + 1
					Escribir "___________________________________"
					Escribir "Se devuelven monedas: " , monedas[i]
					ingreso <- ingreso - monedas[i]
				FinSi
			Fin Si
		Fin Para
	Hasta Que precio == ingreso
	
Fin Funcion

Funcion cantidad <- cobrar ( precio )
	ingreso <- 0
	
	Dimension monedasValidas[3]
	monedasValidas[1] <- 10
	monedasValidas[2] <- 50
	monedasValidas[3] <- 100
	
	Mientras ingreso < precio Hacer
		bandera <- 0
		operaciones<-0
		cantidad<-0
		Escribir "Ingrese monedas (10, 50, 100)"
		Leer ingreso_nuevo
		
		Para i<-1 Hasta 3 Con Paso 1 Hacer
			Si ingreso_nuevo == monedasValidas[i] Entonces
				bandera <- 1
			FinSi
		FinPara
		
		Si bandera == 1 Entonces
			ingreso <- ingreso + ingreso_nuevo
			Si ingreso > precio Entonces
				Escribir "Se recibio un monto total de ", ingreso
				Escribir "Se cobrara del producto seleccionado la cantidad ", precio
				operaciones <- obtenerCambio(precio, ingreso)
				cantidad <- operaciones
				Escribir "___________________________________"
				Escribir "Operaciones realizadas para obtener cambio en esta compra: ", operaciones
			SiNo
				Si ingreso == precio Entonces
					Escribir "Producto pagado."
				FinSi
			Fin Si
		SiNo
			Escribir "Moneda no valida, favor de ingresar otra cantidad." 
		FinSi
	Fin Mientras
	
Fin Funcion

Funcion elegirProducto ( )
	productoA <- 270
	productoB <- 340
	productoC <- 390
	menu <- 0
	cantidadCompras<-0
	cantidadOperaciones<-0
	Escribir "Ingrese nombre de usuario."
	Leer nombre
	
	Mientras menu < 1 Hacer
		Escribir "___________________________________"
		Escribir "Seleccione la opcion de producto a comprar."
		Escribir "A) primer producto - 270"
		Escribir "B) segundo producto - 340"
		Escribir "C) tercer producto - 390"
		Escribir "D) Salir"
		Escribir "___________________________________"
		Leer productoSeleccionado
		
		Segun productoSeleccionado Hacer
			"A":
				cantidadCompras <- cantidadCompras + 1
				cantidadOperaciones <- cantidadOperaciones + cobrar(productoA)
			"B":
				cantidadCompras <- cantidadCompras + 1
				cantidadOperaciones <- cantidadOperaciones + cobrar(productoB)
			"C":
				cantidadCompras <- cantidadCompras + 1
				cantidadOperaciones <- cantidadOperaciones + cobrar(productoC)
			"D":
				menu <- 1
		Fin Segun
	FinMientras
	Escribir "El cliente ", nombre, " realizo ", cantidadCompras, " compras con un total de ", cantidadOperaciones, " operaciones"
Fin Funcion

Algoritmo examen1
	elegirProducto()
	
FinAlgoritmo
