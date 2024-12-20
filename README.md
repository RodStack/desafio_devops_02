# Desafio DevOps Modulo 5 - 01

En este proyecto cree una infraestructura en la nube con Amazon Web Services (AWS). Configurando una VPC (Virtual Private Cloud) con 4 subredes (2 públicas y 2 privadas), permitiendo un acceso controlado a Internet y asegurando que los recursos más sensibles estén protegidos.
## Pasos Realizados
1. **Creación de la VPC**  
   - Configuré una VPC con el CIDR Block `10.0.0.0/24`, lo que me da un rango de direcciones IP de 256.
   - Dentro de esta VPC, creé 4 subredes: 2 públicas (con acceso a Internet) y 2 privadas.
2. **Grupos de Seguridad**  
   - Configuré un grupo de seguridad para restringir las conexiones, permitiendo solo el acceso SSH.
3. **Generación de Clave PEM**  
   - Creé una clave PEM para autenticar las conexiones SSH a las instancias EC2, y la guardé de manera segura para evitar accesos no autorizados.
4. **Configuración de Instancia EC2**  
   - Utilicé una instancia `t2.micro` para pruebas. Esta instancia es económica y adecuada para entornos de desarrollo.
---
## GitHub Actions
Ahora, explico el flujo de trabajo de GitHub Actions que automatiza la creación de la instancia EC2:
### ¿Por qué usar secretos y variables?
1. **Secretos en GitHub**  
   Los secretos como `AWS_ACCESS_KEY_ID` y `AWS_SECRET_ACCESS_KEY` se utilizan para mantener las credenciales de AWS seguras. No quiero que estas claves se expongan públicamente en mi repositorio, así que las guardo en **GitHub Secrets**. De esta manera, las puedo usar de forma segura sin comprometer la seguridad de mi proyecto.
2. **Variables en GitHub Actions**  
   Las variables como `MY_AMI`, `MY_KEY`, `MY_SG`, y `MY_REGION` me permiten centralizar y reutilizar valores importantes, como la imagen de la máquina, la clave SSH, el grupo de seguridad y la región de AWS, sin tener que escribirlos varias veces. Esto hace que el flujo de trabajo sea más limpio y fácil de modificar en el futuro.
