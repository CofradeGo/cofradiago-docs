# Endpoint: Login DMG / Auxiliar

**URL:** `/auth/login/:domain`  
**Método:** `POST`  
**Descripción:** Permite que un usuario DMG o Auxiliar se autentique dentro de una Hermandad y reciba un JWT válido.

---

## Path Parameters

| Parámetro | Tipo   | Descripción                  |
|-----------|--------|------------------------------|
| domain    | string | Dominio de la Hermandad (ej: `soledad`) |

---

## Body (JSON)

| Campo    | Tipo   | Obligatorio | Descripción                        |
|----------|--------|------------|------------------------------------|
| username | string | Sí         | Nombre de usuario (DMG o Auxiliar) |
| password | string | Sí         | Contraseña del usuario             |

---

## Respuestas

### 200 OK

**Condición:** Login correcto.  
**Body:**

```json
{
  "token": "<JWT_TOKEN>"
}
