---
layout: single
title: Active Directory Hardening - inicio 01
excerpt: "Mis inicio con Active Directory (AD) donde describo mi experiencia de seguridad con este"
date: 2023-02-09
classes: wide
header:
  teaser: /assets/images/active-directory/active-directory-logo.png
  teaser_home_page: true
categories:
  - Investigación
  - infosec
tags:
  - activedirectory
---

![](/assets/images/active-directory/active-directory-logo.png)

# **¿Como iniciar en Active Directory (AD)? - Mi Camino**

En esta entonces solo tenía 16 horas para aprender sobre AD, si suena muy poco tiempo para aprender sobre este servicio de directorio, antes de empezar el AD Microsoft lo define como "un directorio que es una estructura jerárquica que almacena información sobre objetos en la red". Partiendo de esta definición, nosotros los del área de seguridad necesitamos ponernos en marcha rápido y de manera eficiente, para ello los pasos que realice fueron los siguientes:
1. Soy fans de Tryhackme, lo que hice fue buscar un curso de AD aquí; y lo encontré se llama ([Active Directory Basics](https://tryhackme.com/room/winadbasics))
2. Luego de aprender los fundamentos era necesario obtener estándares para definir una línea base de seguridad inicial en un AD. En este caso utilice las recomendaciones de seguridad que ofrece ADSecurity y el CIS (más adelante definimos estos).
3. Manos a la obra, para generar un pequeño laboratorio utilice una máquina virtual (VM) con la imagen ISO de Windows Server 2019. (más adelante explico esto).
4. Esta fase es muy importante y es conocer como aplicar las recomendaciones de seguridad y qué metodología utilizar para este.

Lo que debemos de saber antes de leer por completo este post:
> 1. Esto es una guía de herramientas y documentación que te ahorraran tiempo al momento de aprender del AD.
> 2. No entro en detalles de técnicos como configuraciones de máquina virtual e instalación de la imagen ISO.
> 3. No doy los resultados del curso de tryhackme de active directory basics.

## **FUNDAMENTO DE ACTIVE DIRECTORY**
Necesitaba aprender rápido sobre los fundamentos de AD para ello utilice el curso de Tryhackme ([Active Directory Basics](https://tryhackme.com/room/winadbasics)) esta muy bueno, te enseña lo primordial y el contenido es de mi primera mano por expertos en seguridad. En este momento esta sala es gratis. Si no conoces mucho sobre Tryhackme te recomiendo que lo investigues y te registres en esta plataforma de seguridad. El curso no toma mucho tiempo, vas practicando en la marcha y te da los fundamentos más importantes del AD.

## **ENTORNO DE TRABAJO** 
Ahora bien, yo quería aprender a instalar desde cero un AD pero para ello necesitas un sistema operativo de Windows, el recomendado es Windows Server, yo selección la versión 2019. Esta instalación la realice en una VM de mi maquina local. Los recursos que utilice son los siguientes:
VM: ([VMware Workstation Player](https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html)) para Windows.
Imagen ISO: Sesión de prueba mayor a 90 días si no me equivoco ([Windows Server 2019 | Centro de evaluación de Microsoft]( https://www.microsoft.com/es-es/evalcenter/evaluate-windows-server-2019))
Busca como instalar la Imagen ISO de Windows Server 2019 en algún tutorial de tu preferencia. Ejemplo: Youtube
Instalación del AD: para esta actividad utilice la documentación oficial de Microsoft, es una buena practica seguir la documentación oficial, sin embargo, en mi caso lo complemento con algún tutorial en Youtube pero validando cada paso que se realiza. ([Documentación de Microsoft – Install AD]( https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/install-active-directory-domain-services--level-100-#BKMK_GUI))

## **LÍNEA BASE DE SEGURIDAD (HARDENING)**
> Para establecer una línea base de seguridad utilice la guía del CIS y ADSecuirty. 
> 1. Centro de Seguridad de Internet (CIS) la empresa AWS los define como “un conjunto de prácticas recomendadas reconocidas y consensuadas a nivel mundial para ayudar a los profesionales de la seguridad a aplicar y administrar las medidas de protección de seguridad cibernética. Desarrolladas en colaboración con una comunidad mundial de expertos en seguridad, estas directrices ayudan a las organizaciones a protegerse de forma proactiva contra los riesgos emergentes. Las empresas aplican las directrices de los puntos de referencia del CIS para limitar las vulnerabilidades de seguridad basadas en la configuración de los activos digitales.”  ([CIS](https://www.cisecurity.org/cis-benchmarks))
> 2. La gente de ADSecuirty es una página web sección “acerca de” nos dice: Sean Metcalf (@PyroTek3) es un Microsoft Certified Master (MCM) / Microsoft Certified Solutions Master (MCSM) en servicios de directorio (Active Directory Windows Server 2008 R2), que es un grupo de élite de expertos en Active Directory (solo alrededor de 100 en todo el mundo). Sean realiza investigaciones de seguridad centradas en la plataforma de Microsoft y ha identificado un comportamiento interesante de Kerberos, así como otras investigaciones únicas. Ha hablado sobre ataque y defensa de Active Directory en BSides Charm (Baltimore), Shakacon, Black Hat USA 2015, Black Hat USA 2016, DEF CON 23 (2015), DEF CON 24 (2016) y conferencias de seguridad DerbyCon. Las diapositivas y videos (si están disponibles) de estas presentaciones se pueden encontrar en la página de Presentaciones. ([ADSecurity]( https://adsecurity.org/?p=3377 ))

## **Metodología para aplicar recomedanciones:**
Utilizar un procedimiento para implementar políticas en un AD.
1. Planificación: comprender la estructura organizativa (uso de software o hardware).
2. Diseño de las políticas: defina el entorno de aplicación de las políticas (aplica a usuarios corporativos, clasifique a los usuarios, computadores, ubicaciones, requerimientos del usuarios y computadoras).
3. Implementación: inicie en un entorno de prueba controlado. La implementación es considerada critica, por tal razón pruebe minuciosamente. Implemente pequeños bloques de políticas y verifique que todo funcione bien. 
4. Mantenimiento: establecer procedimientos de control para trabajar a nivel de GPO. Ejemplo: modificaciones, mejoras, etc.
5. Emplear la Guía del CIS.
6. Implementar según los requerimientos del cliente.
7. Comprender y probar cada recomendación del CIS cuidadosamente.
8. Comprender las ventajas y desventajas de cada una de las recomendaciones a implementar.
9. Realizar Backup de las GPO.

https://learn.microsoft.com/en-us/previous-versions/technet-magazine/cc137720(v=msdn.10)?redirectedfrom=MSDN

Otras recomendaciones similares sobre best practice al implementar una GPO:
Implementar las Mejores Prácticas (Best Practices) en la creación de GPO (Group Policy Object) en Active Directory puede ayudar a garantizar que la implementación de políticas de grupo sea eficiente y efectiva. A continuación, se presentan algunas de las mejores prácticas que se deben tener en cuenta al crear y aplicar GPO:
1. Planificación y diseño: Antes de crear GPO, es importante realizar una planificación y diseño cuidadosos. Esto incluye definir objetivos claros para la implementación de políticas de grupo, identificar las configuraciones necesarias y las restricciones que puedan afectar la implementación.
2. Jerarquía de GPO: Organizar GPO en una jerarquía clara puede simplificar la administración y la aplicación de políticas de grupo. Se recomienda que se siga una estructura en cascada, donde los GPO de nivel superior contienen políticas generales, y los de nivel inferior contienen configuraciones más específicas.
3. Seguridad: Las políticas de seguridad de GPO son una de las partes más importantes de su implementación. Se recomienda utilizar permisos de seguridad para asegurarse de que solo los usuarios y grupos adecuados tengan acceso a los GPO. Además, se deben utilizar configuraciones de seguridad fuertes para prevenir la manipulación de GPO.
4. Control de versiones: Es importante mantener un control de versiones en GPO para asegurarse de que se realicen cambios de forma controlada y documentada. Se recomienda mantener un registro de todos los cambios y actualizar la documentación correspondiente.
5. Pruebas: Antes de implementar GPO en un entorno de producción, es importante realizar pruebas exhaustivas en un entorno de prueba. Esto ayuda a garantizar que las políticas de grupo se implementen correctamente y que no causen problemas en el entorno de producción.
6. Documentación: Documentar todos los detalles relacionados con GPO es crucial para una administración efectiva y sostenible. Se recomienda mantener un registro de todos los cambios realizados, la razón de dichos cambios, la fecha de implementación, entre otros.
7. Actualizaciones: Las políticas de grupo deben actualizarse regularmente para mantenerse al día con los cambios en el entorno de red. Se recomienda programar revisiones periódicas y documentar cualquier cambio implementado.
Al seguir estas mejores prácticas, puede implementar GPO de manera eficiente y efectiva en Active Directory.



**¡Saludos!**

#### Rubén González