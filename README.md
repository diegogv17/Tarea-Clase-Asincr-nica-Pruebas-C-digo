# Tarea: pruebas (unidad, integración y E2E)

## Una frase por error

1. **`diasEntre`**: sumaba un `+1` que contaba también el último día. Lo delató `cuenta el primer día y no cuenta el último`.
2. **`aplicarCupon`**: un cupón mayor que la factura la dejaba en negativo; ahora el resultado tiene piso en 0. Lo delató `nunca deja el cobro en negativo`.
3. **`calcularTotal`**: calculaba el IVA sobre el precio de lista; ahora descuenta primero y aplica el IVA sobre el neto. Lo delató `el IVA se calcula sobre lo que de verdad se cobra`.
4. **`suscripcionesActivas`**: le faltaba `AND estado = 'activa'`, devolvía canceladas y morosas. Lo delató `devuelve solo las activas del equipo`.
5. **`canjearCupon`**: leía el cupo y escribía después, y los canjes simultáneos se colaban; ahora decisión y escritura son una sola sentencia SQL atómica. Lo delató `respeta el límite cuando llegan diez al mismo tiempo`.
6. **Pantalla de pago**: mostraba `subtotal + iva` e ignoraba el descuento; ahora muestra `desglose.total`. Lo delató el spec `el total que ve el cliente es el total que se le cobra`.

## Resultados

- Unidad e integración: 36 pruebas en verde
- Mutantes: 6 de 6 cazados
- E2E: 5 de 5 en verde
- Lint y tipos: sin errores
- Cobertura: 94% de líneas, 100% de funciones
