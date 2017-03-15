---
title: "Probar &#225;rea 7: recurso compartido | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente [Visual Studio SDK], compartir elementos"
  - "compartir elementos de origen control plug-ins,"
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Probar &#225;rea 7: recurso compartido
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta área de prueba cubre compartir elementos entre las ubicaciones mediante el comando de **Compartir** .  
  
 Una operación de hhare es la duplicación manifiesto de archivos y los elementos de la carpeta entre dos o más ubicaciones dentro de una jerarquía de archivos de control de código fuente.  La duplicación no aparece realmente en el servidor, pero el usuario ve el mismo archivo en varias ubicaciones especificadas.  Siempre que se realicen a los elementos compartidos cualquiera de los, esos cambios aparecen en el resto de las ubicaciones compartidas.  
  
 El uso compartido en carpetas funciona si selecciona una carpeta con al menos un archivo con control de código fuente en él.  Deshabilite el comando de la acción en las condiciones siguientes:  
  
-   Si la carpeta seleccionada es una carpeta vacía.  
  
-   Si hay una carpeta real, pero no contiene ningún archivo de control de código fuente.  
  
-   Si hay una carpeta virtual, si los archivos bajo control de código fuente se en él o no.  
  
-   Si hay un proyecto web del sitio remoto.  
  
## menú de comandos Access  
 Las siguientes rutas de menú del entorno de desarrollo integrado de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se utilizan en los casos de prueba.  
  
 acción: **Archivo**\- \>**Control de código fuente**\- \>**Compartir**.  
  
## El comportamiento esperado  
  
-   el archivo compartido aparece en la ubicación compartida.  
  
-   Ver el historial del almacén de versiones del control de código fuente muestra que los archivos están compartidos.  
  
-   Editar un archivo compartido modifica ambas ubicaciones del archivo.  
  
## Casos de prueba  
 Los siguientes son casos de prueba concretos para el área de prueba de la acción.  
  
|Acción|Pasos de prueba|Resultados esperado a comprobar|  
|------------|---------------------|-------------------------------------|  
|Compartir un archivo en un proyecto cargado bajo control de código fuente a otro proyecto cargado|1.  Cree un nuevo proyecto.<br />2.  agregue un segundo proyecto a la solución.<br />3.  Cree un archivo en el segundo proyecto con un nombre que no entre en el primer proyecto.<br />4.  Agregar la solución al control de código fuente.<br />5.  Seleccione el primer proyecto.<br />6.  cuadro de diálogo abierto de **Compartir** \(**Archivo** \- \> **Control de código fuente** \- \> **Compartir**\).<br />7.  Compartir el archivo del segundo proyecto el primer proyecto.<br />8.  Acepte **Desproteger** si se le solicita.|El comportamiento esperado común.|  
|Compartir un archivo en un proyecto a otro|1.  Cree un nuevo proyecto.<br />2.  Agréguela al control.<br />3.  Cierre la solución.<br />4.  Cree un segundo proyecto \(la nueva solución\).<br />5.  Agregar la solución al control de código fuente.<br />6.  Seleccione el proyecto.<br />7.  Abra el cuadro de diálogo de **Compartir** \(**Archivo** \- \> **Control de código fuente** \- \> **Compartir**\).<br />8.  Compartir un archivo de proyecto previamente agregado al proyecto abierto.<br />9. Acepte **Desproteger** si se le solicita.|El comportamiento esperado común.|  
|Compartir una parte del archivo no el proyecto de control de código fuente del proyecto actualmente cargado|1.  Cree un nuevo proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Agregue un archivo al control de código fuente que no forma parte del proyecto o la solución.<br />4.  Seleccione el proyecto y abra el cuadro de diálogo de **Compartir** \(**Archivo** \- \> **Control de código fuente** \- \> **Compartir**\).<br />5.  Seleccione un archivo en el cuadro de diálogo de **Compartir** que no existe en el proyecto o la solución actual y no compartirla.<br />6.  Acepte **Desproteger** si se le solicita.|El almacén de control de código fuente ha realizado una obtener, por lo que el archivo está en la ubicación local del proyecto.|  
|Compartir archivos dentro del mismo proyecto a una carpeta diferente|1.  **Desproteger automáticamente** seleccione en **Herramientas** \- \> **Opciones** \- \> **Control de código fuente**.<br />2.  Cree un nuevo proyecto y agréguela al control.<br />3.  Agregue una carpeta al proyecto.<br />4.  Agregue un archivo en la carpeta y proteger la carpeta.<br />5.  Seleccione la carpeta.<br />6.  cuadro de diálogo abierto de **Compartir** \(**Archivo** \- \> **Control de código fuente** \- \> **Compartir**\).<br />7.  Archivo de la acción en la carpeta seleccionada.|El comportamiento esperado común.<br /><br /> La carpeta se debe proteger con un archivo en él antes de poder utilizar para la acción.|  
|Compartir una carpeta en el proyecto cargado — Recursivos|1.  Cree un nuevo proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Seleccione el proyecto.<br />4.  Abra el cuadro de diálogo de **Compartir** \(**Archivo** \- \> **Control de código fuente** \- \> **Compartir**\).<br />5.  Seleccione una carpeta.<br />6.  Comparta la carpeta de forma recursiva en el proyecto.|El comportamiento esperado común.|  
|Compartir varios archivos de un proyecto a otro|1.  cree un nuevo proyecto con varios archivos en él.<br />2.  Agregar la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  cree un nuevo proyecto en una nueva solución.<br />5.  Agregar la solución al control de código fuente.<br />6.  Seleccione el proyecto.<br />7.  Abra el cuadro de diálogo de **Compartir** \(**Archivo** \- \> **Control de código fuente** \- \> **Compartir**\).<br />8.  Compartir varios archivos del proyecto creado previamente al proyecto abierto.|El comportamiento esperado común.|  
  
## Vea también  
 [Guía de pruebas para los complementos de Control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)