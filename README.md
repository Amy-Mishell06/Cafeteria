# Dulce Café - Registro de Compras

Aplicación móvil desarrollada en **Ionic** que permite registrar la compra de un producto de una cafetería y calcular el pago, aplicando un descuento y mostrando el cambio o el saldo pendiente.

**Fecha:** 15/10/2026

---

## Tecnologías utilizadas

- Ionic 9
- Angular 22 (componentes standalone)
- Capacitor 8
- @capacitor/assets (generación del ícono y splash screen)
- @capacitor/splash-screen
- Android Studio

---

## Funcionalidades

### Pantalla de inicio
Muestra una imagen de portada con el nombre de la cafetería y un botón **Iniciar** para entrar al sistema.

### Pestaña Compra
Solicita:
- Nombre del producto
- Cantidad
- Precio unitario

Al enviar el formulario se validan los datos. Si son correctos, se guarda la compra y se abre automáticamente la pestaña **Pago**.

### Pestaña Pago
Muestra el producto y el subtotal recibido, y solicita:
- Descuento (%)
- Dinero entregado por el cliente

Al presionar **Calcular** se muestra el total final y el **cambio** o el **saldo pendiente**.

---

## Validaciones

| Campo | Regla |
|---|---|
| Nombre del producto | Obligatorio |
| Cantidad | Número entero mayor que 0 |
| Precio unitario | Mayor que 0 |
| Descuento | Entre 0 y 100 |
| Dinero recibido | Mayor o igual a 0 |

Si algún dato no es válido, se muestra un mensaje de error y no se continúa.

---

## Cálculos

```
Subtotal   = cantidad × precio unitario
Descuento  = subtotal × porcentaje / 100
Total      = subtotal − descuento
Diferencia = dinero recibido − total
```

- Si la diferencia es mayor o igual a 0 → se muestra el **cambio**.
- Si la diferencia es menor a 0 → se muestra el **saldo pendiente**.

**Ejemplo:** 3 capuchinos a $2.50 con 10% de descuento
Subtotal $7.50 → Descuento $0.75 → Total $6.75 → Si el cliente entrega $10, el cambio es $3.25.

---

## Íconos y pantalla de inicio

- **Íconos de pestañas:** imágenes personalizadas para Compra (taza) y Pago (billetera), ubicadas en `src/assets/icons/`.
- **Ícono de la app y splash screen:** generados con `@capacitor/assets` a partir de las imágenes de la carpeta `assets/`:
  - `icon-only.png` (1024×1024)
  - `splash.png` y `splash-dark.png` (2732×2732)

Comando utilizado:
```bash
npx capacitor-assets generate --android
```

---

## Estructura del proyecto

```
compras/
├── assets/                  # Imágenes para generar ícono y splash
├── docs/                    # Capturas y video de evidencia
├── android/                 # Proyecto nativo de Android
└── src/
    ├── app/
    │   ├── inicio/          # Pantalla de inicio
    │   ├── tab1/            # Pestaña Compra
    │   ├── tab2/            # Pestaña Pago
    │   ├── tabs/            # Barra de pestañas
    │   └── services/
    │       └── compra.service.ts   # Comparte los datos entre pestañas
    ├── assets/
    │   ├── icons/           # Íconos de las pestañas
    │   └── img/             # Imágenes de la app
    └── global.scss          # Colores y estilos generales
```

---

## Evidencias

### Ícono de la aplicación
<img width="203" height="265" alt="WhatsApp Image 2026-10-15 at 12 56 41 AM" src="https://github.com/user-attachments/assets/ffd76dd4-c580-4874-a440-e698f6dd3fe7" />

### Pantalla de inicio
<img width="750" height="1600" alt="WhatsApp Image 2026-10-15 at 12 56 41 AM (1)" src="https://github.com/user-attachments/assets/410bc785-8ef5-4b0a-9f82-dd2f876adec9" />

### Pestaña Compra
<img width="750" height="1602" alt="WhatsApp Image 2026-10-15 at 12 56 41 AM (2)" src="https://github.com/user-attachments/assets/0abfc7e7-db79-4b0a-920e-4793dc0f7113" />
<img width="752" height="1601" alt="WhatsApp Image 2026-10-15 at 12 56 41 AM (4)" src="https://github.com/user-attachments/assets/c2f4bddb-a457-4631-8032-72e89978049d" />
<img width="752" height="1598" alt="WhatsApp Image 2026-10-15 at 12 56 41 AM (5)" src="https://github.com/user-attachments/assets/7ae6916d-dabc-484a-8d1c-c2dfe478bb53" />


### Pestaña Pago
<img width="750" height="1600" alt="WhatsApp Image 2026-10-15 at 12 56 41 AM (3)" src="https://github.com/user-attachments/assets/2a081315-6661-4f55-9155-983e33738072" />
<img width="748" height="1599" alt="WhatsApp Image 2026-10-15 at 12 56 41 AM (6)" src="https://github.com/user-attachments/assets/3c325997-0dab-453b-829f-49e77527d1fa" />

