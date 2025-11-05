##  Modelo de Actividades – Registrar una Venta

### Descripción General

El **modelo de actividades** representa el flujo de acciones que se llevan a cabo durante el proceso de **registrar una venta** en el sistema **DulceAdmin**.  
En este proceso interactúan principalmente el **Trabajador (Cajero)**, el **Sistema DulceAdmin**, y la **Base de Datos / Inventario**.

El objetivo del modelo es mostrar cómo se orquestan las decisiones y tareas necesarias para generar correctamente un recibo de venta, validar la información del cliente, calcular totales y actualizar el inventario.

---

### Actores Involucrados

- **Trabajador (Cajero):** Encargado de iniciar el proceso de venta, seleccionar productos, ingresar datos y confirmar el pago.  
- **Sistema DulceAdmin:** Procesa la información, calcula totales, valida stock, genera el recibo y gestiona los cambios de estado.  
- **Base de Datos / Inventario:** Actualiza las existencias de los productos después de confirmar la venta.

---

### Flujo de Actividades

1. **Inicio del proceso:** El trabajador accede al sistema y selecciona la opción “Registrar venta”.  
2. **Ingreso de datos del cliente:** Se busca al cliente en la base de datos.  
   - Si existe → se continúa con la venta.  
   - Si no existe → se registra un nuevo cliente.  
3. **Selección de productos:** El trabajador elige los productos que el cliente desea comprar y especifica las cantidades.  
4. **Verificación de stock:**  
   - Si hay suficiente stock → continúa el proceso.  
   - Si no hay → se modifica la cantidad hasta alcanzar la disponibilidad.  
5. **Cálculo del total:** El sistema calcula el total de la venta con base en los precios y cantidades.  
6. **Selección del método de pago:** El trabajador elige cómo se pagará (efectivo, tarjeta, etc.).  
7. **Confirmación de la venta:** Se confirma el registro de la venta y se genera el recibo.  
8. **Actualización del inventario:** El sistema descuenta del inventario las unidades vendidas.  
9. **Mensaje de confirmación:** Se muestra al trabajador un mensaje de éxito indicando que la venta fue registrada correctamente.  
10. **Fin del proceso.**

---

### Decisiones Importantes

- **¿Cliente existe?**  
  Determina si se debe registrar un nuevo cliente o usar uno existente.  
- **¿Hay stock disponible?**  
  Evita vender productos con inventario insuficiente.  
  Si no hay stock suficiente, se ajusta la cantidad y se recalcula el total.

---


### Diagrama del Modelo de Actividades

![Modelo de Actividades - Registrar una Venta](img\ModeloActividades(RegistrarUnaVenta).png)

---

### Resultados del Proceso

- Recibo generado y almacenado en el sistema.  
- Inventario actualizado.  
- Validación del cliente (creado o reutilizado).  
- Confirmación visual para el trabajador.

---

### Conclusión

El modelo de actividades demuestra de forma clara cómo el sistema DulceAdmin coordina tareas automáticas y manuales en el proceso de venta.  
La secuencia asegura la integridad de los datos, la consistencia del inventario y una correcta facturación para cada transacción.

[ir al inicio](/README.md).

[Ir al anterior](MER.md).

[Modelo de clases](Modelo_Clases.md).