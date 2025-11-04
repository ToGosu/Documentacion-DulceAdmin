## Modelo de Estados – Recibo

### Descripción General

El **modelo de estados** del sistema **DulceAdmin** describe los diferentes **estados por los que pasa un Recibo** desde su creación hasta su finalización o cancelación.  
Permite entender cómo cambia su estado en función de las acciones realizadas por el trabajador o el sistema.

---

### Estados Principales

| Estado | Descripción |
|--------|--------------|
| **Inicio** | El proceso de creación del recibo comienza. |
| **Creado** | El recibo se genera con la información del cliente, productos y trabajador. |
| **Actualizado** | Se realizan cambios o correcciones antes de confirmarlo. |
| **Pagado** | Se confirma el pago, se registra el método utilizado y se valida el total. |
| **Facturado** | El recibo queda cerrado y se genera la factura final. |
| **Cancelado** | El recibo se anula por error o devolución. |

---

### Transiciones entre Estados

| Estado inicial | Acción / Evento | Estado final |
|----------------|----------------|---------------|
| — | Registrar venta | **Creado** |
| **Creado** | Modificar datos | **Actualizado** |
| **Actualizado** | Confirmar pago | **Pagado** |
| **Pagado** | Generar factura | **Facturado** |
| **Cualquiera** | Anular recibo | **Cancelado** |

---

### Diagrama del Modelo de Estados

![Modelo de Estados - Recibo](img/ModeloEstados(Recibo).png)

---

### Conclusión

El **modelo de estados del Recibo** permite comprender cómo evoluciona el documento a lo largo del proceso de venta, pago y facturación.  
También contempla escenarios de actualización o cancelación, reflejando el comportamiento real del sistema DulceAdmin frente a cambios o errores en las transacciones.