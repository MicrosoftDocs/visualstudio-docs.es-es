---
title: "Propiedades de archivo, JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "javascript.project.property.expandedsdknode.fileversion"
  - "javascript.project.property.expandedsdknode.uri"
  - "javascript.project.property.expandedsdknode.filename"
  - "javascript.project.property.reference.description"
  - "javascript.project.property.reference.specificversion"
  - "javascript.project.property.reference.identity"
  - "javascript.project.property.fullpath"
  - "javascript.project.property.packageaction"
  - "javascript.project.property.reference.package"
  - "javascript.project.property.copytooutputdirectory"
  - "javascript.project.property.expandedsdknode.sdkpath"
  - "javascript.project.property.reference.filetype"
  - "javascript.project.property.reference.culture"
  - "javascript.project.property.filename"
  - "javascript.project.property.reference.resolvedpath"
  - "javascript.project.property.reference.version"
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Propiedades de archivo, JavaScript
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Puede utilizar las propiedades de archivo para indicar qué acciones debe ejecutar sobre los archivos el sistema del proyecto.  Por ejemplo, puede establecer propiedades de archivo para indicar si un archivo se debe agregar al paquete como un archivo de recursos.  
  
 Puede seleccionar cualquier archivo en el Explorador de soluciones y, a continuación, examinar sus propiedades en la ventana Propiedades.  Los archivos JavaScript tienen cuatro propiedades: **Copiar en el directorio de resultados**, **Acción del paquete**, **Nombre de archivo**, y **Ruta de acceso del archivo**.  
  
## Propiedades de archivo  
 Esta sección describe las propiedades comunes a los archivos JavaScript.  
  
### Copiar en el directorio de resultados \(Propiedad\)  
 Esta propiedad especifica las condiciones en las que el archivo de código fuente seleccionado se copiará en el directorio de salida.  Seleccione **No copiar** si el archivo nunca se va a copiar en el directorio de resultados.  Seleccione **Copiar siempre** si el archivo siempre se copiará en el directorio de resultados.  Seleccione **Copiar si es posterior** si el archivo sólo se copiará cuando sea más reciente que un archivo con el mismo nombre que esté presente en el directorio de resultados.  
  
### Acción del paquete  
 La propiedad **Acción del paquete** indica qué hace Visual Studio con un archivo cuando se ejecuta una compilación.  **Acción del paquete** puede tener uno o varios valores:  
  
-   **Ninguno** \- El archivo no no se incluye en el manifiesto del paquete.  Un ejemplo es un archivo de texto que contenga documentación, como un archivo Léame.  
  
-   **Contenido** \- El archivo no se incluye en el manifiesto del paquete.  Por ejemplo, este valor es el predeterminado de .htm, un .js, un .css, una imagen, un sonido, o un archivo de vídeo.  
  
-   **Manifiesto** – El archivo no no se incluye en el manifiesto del paquete.  En su lugar, el archivo se utiliza para la entrada al generar el manifiesto del paquete.  Éste es el valor predeterminado del archivo de package.appxmanifest.  
  
-   **Recurso** \- El archivo no no se incluye en el manifiesto del paquete.  En su lugar, el contenido del archivo se indizan en el índice \(PRI\) del paquete que el manifiesto del paquete.  Este valor se utiliza normalmente para los archivos de recursos.  
  
 El valor predeterminado para **Acción del paquete** depende de la extensión de archivo que agregue a la solución.  
  
### Nombre de archivo \(Propiedad\)  
 Muestra el nombre de archivo como valor de solo lectura.  Para cambiar el nombre del archivo, se debe clic con el botón secundario en el explorador de soluciones y **Cambiar nombre**seleccione.  
  
### Propiedad de la ruta de acceso completa  
 Muestra la ruta de acceso completa al archivo como valor de solo lectura.  Para cambiar la ruta de acceso del archivo, puede arrastrar y colocar el archivo en el explorador de soluciones.  
  
## Propiedades de archivo de referencia  
 Esta sección describe las propiedades comunes a los archivos de referencia [!INCLUDE[win8_app_js](../../ide/reference/includes/win8_app_js_md.md)].  Al seleccionar una referencia como un archivo de .winmd, una referencia de SDK, una referencia de proyecto\-a\- proyecto, o una referencia de ensamblado en el explorador de soluciones, otras propiedades pueden mostrar en la ventana Propiedades, como el tipo de archivo.  
  
### Referencia cultural  
 Muestra el idioma asociado a la referencia.  
  
### Tipo de archivo  
 Muestra el tipo de archivo de referencia.  
  
### Versión de archivo  
 Muestra la versión del archivo de referencia.  
  
### Identidad  
 Muestra la identidad de referencia que se utiliza en el proyecto, que se almacena en el archivo de proyecto.  
  
### Paquete  
 Muestra el nombre del asociado manifiesto del paquete con la referencia.  
  
### Ruta resueltos  
 Muestra la ruta de acceso a la referencia que se utiliza en el proyecto.  
  
### Ruta de SDK  
 Muestra la ruta de acceso al archivo de referencia de SDK.  
  
### Uri  
 Muestra el identificador URI que se debe incluir en los archivos HTML o JavaScript de proyecto para incluir el archivo como un archivo de código fuente.  
  
### Versión  
 Muestra la versión de referencia.  
  
## Vea también  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/es-es/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)