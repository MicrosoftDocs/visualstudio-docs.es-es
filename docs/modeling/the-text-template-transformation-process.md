---
title: "The Text Template Transformation Process | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, transformation process"
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 30
---
# The Text Template Transformation Process
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El proceso de transformación de plantillas de texto toma un archivo de plantilla de texto como entrada y genera un nuevo archivo de texto como salida.  Por ejemplo, puede utilizar plantillas de texto para generar código de Visual Basic o C\# o bien para generar un informe HTML.  
  
 Tres componentes forman parte de este proceso: el motor, el host y los procesadores de directivas.  El motor controla el proceso; interactúa con el host y el procesador de directivas para generar el archivo de salida.  El host proporciona la interacción con el entorno, como buscar archivos y ensamblados.  El procesador de directivas agrega funcionalidad, como leer los datos de un archivo XML o una base de datos.  
  
 El proceso de transformación de plantillas de texto se realiza en dos pasos.  En primer lugar, el motor crea una clase temporal, que se conoce como clase de transformación generada.  Esta clase contiene el código que generan las directivas y los bloques de control.  Después, el motor compila y ejecuta la clase de transformación generada para producir el archivo de salida.  
  
## Componentes  
  
|Componente|Descripción|Se puede personalizar \(Sí\/No\)|  
|----------------|-----------------|--------------------------------------|  
|Motor|El componente de motor controla el proceso de transformación de plantillas de texto.|No.|  
|Host|El host es la interfaz entre el motor y el entorno de usuario.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es un host del proceso de transformación de texto.|Sí.  Puede escribir un host personalizado.|  
|Procesadores de directivas|Los procesadores de directivas son clases que administran las directivas de las plantillas de texto.  Puede utilizar directivas para proporcionar datos a una plantilla de texto desde un origen de entrada.|Sí.  Puede escribir los procesadores de directivas personalizados.|  
  
## El motor  
 El motor recibe la plantilla como una cadena del host, que administra todos los archivos que se utilizan en el proceso de transformación.  A continuación, el motor pide al host que busque cualquier procesador de directivas personalizado y otros aspectos del entorno.  Después, el motor compila y ejecuta la clase de transformación generada.  El motor devuelve el texto generado al host, que normalmente guarda el texto en un archivo.  
  
## El host  
 El host es responsable de todo lo que se relaciona con el entorno fuera del proceso de transformación, incluidas las siguientes operaciones:  
  
-   Buscar archivos de texto y binarios solicitados por el motor o un procesador de directivas.  El host puede buscar en los directorios y la memoria caché global de ensamblados para localizar ensamblados.  El host puede localizar código de procesador de directivas personalizado para el motor.  El host también puede localizar y leer archivos de texto, y devolver su contenido como cadenas.  
  
-   Proporcionar listas de ensamblados y espacios de nombres estándar que se usan en el motor para crear la clase de transformación generada.  
  
-   Proporcionar el dominio de aplicación que se utiliza cuando el motor compila y ejecuta la clase de transformación generada.  Se usa un dominio de aplicación independiente para proteger la aplicación host de los errores del código de plantilla.  
  
-   Escribir el archivo de salida generado.  
  
-   Establecer la extensión predeterminada del archivo de salida generado.  
  
-   Administrar los errores de transformación de plantilla de texto.  Por ejemplo, el host puede mostrar los errores en la interfaz de usuario o escribirlos en un archivo.  \(En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], los errores se muestran en la ventana de mensajes de error.\)  
  
-   Proporcionar un valor de parámetro necesario si un usuario ha llamado a una directiva sin proporcionar un valor.  El procesador de directivas puede especificar el nombre de la directiva y el parámetro, y pedir al host que proporcione un valor predeterminado si dispone de él.  
  
## Directivas y procesadores de directivas  
 Una directiva es un comando de la plantilla de texto.  Proporciona parámetros al proceso de generación.  Por lo general, las directivas definen el origen y el tipo del modelo u otra entrada, y la extensión de nombre de archivo del archivo de salida.  
  
 Un procesador de directivas puede procesar una o más directivas.  Al transformar una plantilla, debe tener instalado un procesador de directivas que se pueda ocupar de las directivas de la plantilla.  
  
 Las directivas funcionan agregando código en la clase de transformación generada.  Se llama a las directivas desde una plantilla de texto y el motor procesa todas las llamadas a directivas cuando crea la clase de transformación generada.  Después de llamar correctamente a una directiva, el resto del código que escribe en la plantilla de texto se puede basar en la funcionalidad que proporciona la directiva.  Por ejemplo, puede realizar la siguiente llamada a la directiva `import` en la plantilla:  
  
 `<#@ import namespace="System.Text" #>`  
  
 El procesador de directivas estándar convierte esto en una instrucción `using` en la clase de transformación generada.  A continuación, puede utilizar la clase `StringBuilder` en el resto del código de plantilla sin calificarlo como `System.Text.StringBuilder`.