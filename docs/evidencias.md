# Evidencias · RA2 SBD (rellenar por el alumnado)

> Completa este documento con capturas/salidas. No incluyas secretos.
> Indica si has usado **Variante A (IAM Role)** o **Variante B (aws configure)**.

## 0) Identificación
- Alumno/a:
- Grupo:
- Variante usada (A/B):
- Región AWS:
- Bucket S3:

---

## 1) S3 privado
- [ ] Captura del bucket (nombre y región)
![1.1 Bucket nombre y región](../img/1.1.png)
- [ ] Captura/confirmación de que **no es público** (Block Public Access o permisos)
![1.2 Bucket privado](../img/1.2.png)
- [ ] Captura del objeto JSON en `data/sensores/`
![1.3 Objeto JSON en data/sensores](../img/1.3.png)

**Notas:**
- Key usada (S3_KEY):

---

## 2) Notebook / Script de subida
- [ ] Captura de la ejecución del notebook/script subiendo a S3
![2.1 Ejecución notebook subida a S3](../img/2.1.png)
- [ ] Enlace o ruta del archivo en el repo (`notebooks/...`)
Ruta en el repositorio:
    `notebooks/generate_upload_iot.ipynb`

Enlace directo en GitHub:
    https://github.com/AlbertoBrMa/ra2-awsacademy-s3-streamlit-starter-template/blob/main/notebooks/generate_upload_iot.ipynb
---

## 3) EC2 y red
- [ ] Captura de la instancia EC2 (Ubuntu 22.04)
![3.1 Instancia EC2 Ubuntu](../img/3.1.png)
- [ ] Captura del Security Group con puerto 8501 abierto (según reglas del lab)
![3.2 Security Group puerto 8501](../img/3.2.png)
- [ ] Salida de `ssh` conectando (sin mostrar claves)
![3.3 Conexión SSH](../img/3.3.png)

---

## 4) Acceso a S3 desde EC2 (sin secretos)
Ejecuta en EC2:

```bash
aws sts get-caller-identity
aws s3 ls s3://<BUCKET>/data/sensores/
```

- [ ] Captura/salida de ambos comandos
![4 Acceso S3 desde EC2](../img/4.png)

---

## 5) Streamlit en EC2
- [ ] Captura de `streamlit hello` funcionando (o `python -c "import streamlit"`)
![5.1 Verificación Streamlit](../img/5.1.png)
- [ ] Captura de instalación de dependencias (`pip install -r requirements.txt`)
![5.2 Instalación dependencias](../img/5.2.png)

---

## 6) Dashboard (funcionalidad)
Incluye capturas donde se vea:

- [ ] Filtro por `sensor_state`
![6.1 Filtro sensor_state](../img/6.1.png)
- [ ] Slider de temperatura
![6.2 Slider temperatura](../img/6.2.png)
- [ ] Tabla filtrada
![6.3 Tabla filtrada](../img/6.3.png)
- [ ] Gráfica línea (temperatura vs tiempo)
![6.4 Gráfica línea temperatura](../img/6.4.png)
- [ ] Gráfica barras (CO₂ por sensor)
![6.5 Gráfica barras CO2](../img/6.5.png)
- [ ] Mapa con sensores
![6.6 Mapa sensores](../img/6.6.png)

---

## 7) Despliegue final
- [ ] Comando usado para arrancar en segundo plano (ej. `nohup` o script)
![7.1 Arranque en segundo plano](../img/7.1.png)
- [ ] Captura del log (`tail -n 50 streamlit.log` o similar)
![7.2 Log streamlit](../img/7.2.png)
- [ ] URL final:

**URL:** `URL: http://100.31.105.61:8501`

- [ ] Captura en navegador accediendo a la URL
![7.4 Dashboard en navegador](../img/7.4.png)

---

## 8) Observaciones (opcional)
- Problemas encontrados y solución:
  Al arrancar en EC2 con `streamlit run app/dashboard.py`, la aplicación fallaba con `ModuleNotFoundError: No module named 'app'`. El problema era que, en esa ejecución, Python no resolvía el paquete raíz `app` en los imports absolutos (`from app.services...`). Se corrigió adaptando los imports en `app/dashboard.py` para soportar ambos contextos: primero intenta `from app.services...` y, si falla, usa `from services...`.
