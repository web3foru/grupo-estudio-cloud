# Sesiones de AWS

## Contenido:
- Sesión 1: Introducción a la nube de AWS
- Sesión 2: Introducción a EC2 & S3

### Sesión 1: Introducción a la nube de AWS
- Objetivos:
	- Fundamentos de AWS Cloud Computing, cuáles son sus beneficios, principios y buenas prácticas.
	- Aprender de manera téorica y práctica con Cloud Quest.
	- Buscar la manera de financiar los voucher de las certificaciones de aws.

- Conceptos básicos:
	- Problemas con los modelos tradicionales:
		- Pague todo los costos que conlleva un data center.
		- Pagar por suministro de energía, enfriamiento, y mantenimiento.
		- Agregar, reemplazar o quitar Hardware cuesta mucho tiempo.
		- Escalamiento limitado.
		- 24/7 monitoreando su infrastructura.
		- ¿Cómo lidiar con desastres?

	- ¿Qués es la nube?
		- Es poder acceder bajo demanda de recursos de TI a través de Internet con un modelo de precios de pago por uso.

	- 5 características de la nube:
		- On-demand self service: usuarios pueden aprovisionar recursos sin la necesidad de hablar con algún provider.
		- Broad network access: recursos disponibles a través de la red.
		- Multi-tenancy and resource pooling: los clientes pueden usar la misma infrasctructura entre ellos con privacidad y seguridad.
		- Rapid elasticity and scalability: Adquirir y disponer de recursos de forma automática y rápida cuando sea necesario.
		- Measured service: Se mide el uso, los usuarios pagan correctamente por lo que han usado.

	- Principales ventajas de la nube:
		- Cambie los gastos de capital por gastos variables.
		- Benefíciese de las economías de escala(más clientes, más aws, más infra, más rebajas, precios reducidos)
		- Deje de adivinar la capacidad (Capacidad insuficiente, sobre aprovisonamiento)
		- Aumente la velocidad y la agilidad.
		- Detenga el gasto en centro de datos(Costos de mantenimiento y administración)
		- Globalícese en minutos.

	- Problemas resueltos con la nube:
		- Flexibility: cambie los tipos de recursos cuando sea necesario.
		- Cost-Effectiveness: pague solo lo que utilice.
		- Scalability: acomodar cargas más grandes haciendo que el hardware sea más fuerte o agregando nodos adicionales.
		- Elasticity: capacidad de ampliar o reducir cuando sea necesario.
		- High-availability and fault-tolerance: aplicación en varios centros de datos.
		- Agility: desarrollar, probar y desplegar aplicaciones de software rápidamente.

	- Modelos de despliegue:
		- On-premise: La implementación de recursos en las instalaciones, mediante herramientas de virtualización y administración de recursos.
		- Cloud: Una aplicación basada en la nube se implementa completamente en la nube y todas las partes de la aplicación se ejecutan en la nube.
		- Hyrbid:  Una implementación híbrida es una forma de conectar la infraestructura y las aplicaciones entre los recursos en la nube y recursos existentes en instalaciones locales.

	- ¿Qué es un centro de datos?:
		- Una ubicación física que almacena servidores físicos y equipos de hardware relacionados. Contiene la infraestructura informática que requieren los sistemas de TI, como servidores, unidades de almacenamiento y equipos de red. Es la instalación física que almacena los datos digitales de cualquier empresa.

	- AWS es un conjunto de centro de datos:
		- AWS cuenta con 34 regiones al rededor de todo el mundo, cada región tiene al menos 3 zonas de disponibilidad aisladas y físicamente separadas. Además cuenta con 108 zonas de disponibilidad, cada zona de disponibilidad es un grupo de uno o más centros de datos con alimentación, redes y conectividad redundantes en una región en AWS.
		- AWS cuenta con más de 600 edge locations, que son puntos de presencia que se utilizan para alojar datos en caché.

	- Well Architected Framework:
		- Operational Excellence: pilar centrado en ejecutar y monitorear los sistemas, y en mejorar continuamente los procesos y procedimientos.
		- Security: un pilar centrado en la protección de la información y los sistemas.
		- Reliability: plar centrado en las cargas de trabjao que desempeñen las funciones previstas y en cómo recuperarse rápidamente de un fallo.
		- Performance Efficiency: pilar centrado en la asignación estructurada y simplificada de los recursos informáticos y de TI.
		- Cost Optimization: pilar centrado en evitar costes innecesarios.
		- Sustainability: pilar centrado en minimizar los impactos ambientales de la ejecución de cargas de trabajo en la nube.

	- AWS Cloud Adoptation Framework (CAF): Te ayuda a construir y ejecutar un plan completo para la transformación digital de tu organización a través de un uso innovador de AWS.
		- Business Perspective: ayuda a garantizar que las inversiones en la nube aceleren su transformación digital y sus resultados comerciales.
		- People Perspective: sirve como puente entre la tecnología y negocio, ayudando a las organizaciones a evolucionar rápidamente centrandose en la cultura, estructura organizacional, liderazgo y fuerza laboral.
		- Governance Perspective: busca maximizar los beneficios organizacionales y minimizar los riesgos relacionados a la transformación digital.
		- Platform Perspective: le ayuda a crear una plataforma de nivel empresarial.
		- Security Perspective: le ayuda a lograr la confidencialidad, integridad y disponibilidad de sus datos y cargas de trabajo en la nube.
		- Operations Perspective: ayuda a garantizar que sus servicios en la nube sean entregados a un nivel que satisfaga las necesidades de su negocio.

### Sesión 2: Introducción a EC2 & S3
- Objetivos:
	- Fundamentos de EC2, cuáles son sus tipos de instancias, precios, autoescalado y el balanceador de cargas.
	- Fundamentos de S3, cuáles son sus beneficios, principios y buenas prácticas.
	- Aprender de manera téorica y práctica con  los laboratorios de EC2 & S3 en Cloud Quest.

- Conceptos básicos:
	- Servicios de cómputo:
		- Instancias:
		[Amazon EC2](https://aws.amazon.com/es/ec2/ "Amazon EC2")
		- Contenedores:
		[Amazon ECS](https://aws.amazon.com/es/ecs/ "Amazon ECS"): es un sistema manejador de contenedores que te permite correr y escalar aplicaciones containerizadas en AWS.
 		[Amazon EKS](https://aws.amazon.com/es/eks/ "Amazon EKS"): es un servicio usado para correr Kubernetes en AWS.
 		[AWS Fargate](https://aws.amazon.com/es/fargate/ "AWS Fargate"): es un motor de computo para contenedores, y puede funcionar con ECS y EKS.
		- Sin servidor:
		[AWS Lambda](https://aws.amazon.com/es/lambda/ "AWS Lambda"): es un servicio que te permite correr código sin necesidad de provisionar o manejar servidores.

	- Tipos de instancias EC2:
		- **General purpose**: recursos balanceados (CPU, Storage, RAM) para diversas cargas de trabajo.
		- **Compute optimized**: tareas de computo intensivo.
		- **Memory optimized**: tareas de memoria intensiva.
		- **Accelerated computing**
		- **Storage optimized**: alto desempeño en almacenamiento

	- Precios de instancias EC2:
		- On demand
		- Saving plans
		- Reserved instances
		- Spot instances
		- Dedicated hosts

	- Servicios de almacenamiento:
		- Objeto:
		[Amazon S3](https://aws.amazon.com/es/s3/ "Amazon S3")
		- Bloques:
		[Amazon EBS](https://aws.amazon.com/es/ebs/ "Amazon EBS"): servicio de almacenamiento en bloques que puedes usar con instancias EC2
		- Sistemas de archivos:
		[AWS EFS](https://aws.amazon.com/es/efs/ "AWS EFS")
		[AWS FSx](https://aws.amazon.com/es/efs/ "AWS FSx")

	- Clases de almacenamiento S3:
		- S3 Standard: diseñado para acceso frecuente a los datos. (At least 3 AZ)
 		- S3 Standard-Infrequent Access(S3 Standard-IA): para datos que no accedes con mucha frecuencia, y que necesitas acceso rapido cuando lo necesites.
		- S3 One zone-Infrequent Access(S3 One Zone-IA): almacena datos en una sola AZ.
		- S3 Intelligent-Tiering: ideal para datos con desconocidos o cambiantes patrones de acceso.
		- S3 Glacier: se usa para archivar datos:
			- S3 Glacier Instant Retrieval: acceso en milisegundos.
			- S3 Glacier Flexible Retrieval: acceso en pocos minutos a horas.
			- S3 Glacier Deep Archive: acceso dentro de 12 horas.