---
title: Propiedades de archivo, JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- javascript.project.property.expandedsdknode.fileversion
- javascript.project.property.expandedsdknode.uri
- javascript.project.property.expandedsdknode.filename
- javascript.project.property.reference.description
- javascript.project.property.reference.specificversion
- javascript.project.property.reference.identity
- javascript.project.property.fullpath
- javascript.project.property.packageaction
- javascript.project.property.reference.package
- javascript.project.property.copytooutputdirectory
- javascript.project.property.expandedsdknode.sdkpath
- javascript.project.property.reference.filetype
- javascript.project.property.reference.culture
- javascript.project.property.filename
- javascript.project.property.reference.resolvedpath
- javascript.project.property.reference.version
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fb3f9dcef138bdb9e0452eb1b739dca652d0844d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567474"
---
# <a name="file-properties-javascript"></a>Propiedades de archivo, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [propiedades de archivo, JavaScript](https://docs.microsoft.com/visualstudio/ide/reference/file-properties-javascript).  
  
  
Puede usar propiedades de archivo para indicar qué acciones debe realizar el sistema del proyecto en los archivos. Por ejemplo, puede establecer propiedades de archivo para indicar si un archivo debe agregarse al paquete como un archivo de recursos.  
  
 Puede seleccionar cualquier archivo del Explorador de soluciones y, después, examinar sus propiedades en la ventana Propiedades. Los archivos de JavaScript tienen cuatro propiedades: **Copiar en el directorio de salida**, **Acción del paquete**, **Nombre de archivo** y **Ruta de acceso del archivo**.  
  
## <a name="file-properties"></a>Propiedades del archivo  
 En esta sección se describen propiedades comunes de los archivos de JavaScript.  
  
### <a name="copy-to-output-directory-property"></a>Propiedad Copiar en el directorio de salida  
 Esta propiedad especifica las condiciones en las que el archivo de origen seleccionado se copiará en el directorio de salida. Seleccione **No copiar** si el archivo nunca se va a copiar en el directorio de salida. Seleccione **Copiar siempre** si el archivo siempre se va a copiar en el directorio de salida. Seleccione **Copiar si es posterior** si el archivo se va a copiar solo cuando sea posterior que un archivo existente del mismo nombre en el directorio de salida.  
  
### <a name="package-action"></a>Acción del paquete  
 La propiedad **Acción del paquete** indica lo que Visual Studio realiza con un archivo cuando se ejecuta una compilación. **Acción del paquete** puede tener uno de varios valores:  
  
-   **Ninguno**: el archivo no está incluido en el manifiesto de paquete. Un ejemplo es un archivo de texto que contiene documentación, como un archivo Léame.  
  
-   **Contenido**: el archivo está incluido en el manifiesto de paquete. Por ejemplo, esta opción es el valor predeterminado para un archivo de vídeo, audio, imagen, .htm, .js o.css.  
  
-   **Manifiesto** : el archivo no está incluido en el manifiesto del paquete. En su lugar, el archivo se usa para la entrada al generar el manifiesto de paquete. Este es el valor predeterminado para el archivo package.appxmanifest.  
  
-   **Recurso**: el archivo no está incluido en el manifiesto de paquete. En su lugar, el contenido del archivo se indexa en el Índice de recursos del paquete (PRI) que se incluye en el manifiesto de paquete. Normalmente se usa para los archivos de recursos.  
  
 El valor predeterminado para **Acción del paquete** depende de la extensión del archivo que agregue a la solución.  
  
### <a name="file-name-property"></a>Propiedad Nombre de archivo  
 Muestra el nombre de archivo como un valor de solo lectura. Para cambiar el nombre del archivo, debe hacer clic con el botón derecho en el Explorador de soluciones y seleccionar **Cambiar nombre**.  
  
### <a name="full-path-property"></a>Propiedad Ruta de acceso completa  
 Muestra la ruta de acceso completa del archivo como un valor de solo lectura. Para cambiar la ruta de acceso del archivo, puede arrastrar y colocar el archivo en el Explorador de soluciones.  
  
## <a name="reference-file-properties"></a>Propiedades de archivo de referencia  
 En esta sección se describen propiedades comunes de los archivos a los que se hace referencia desde [!INCLUDE[win8_app_js](../../includes/win8-app-js-md.md)]. Cuando selecciona una referencia como un archivo .winmd, una referencia del SDK, una referencia de proyecto a proyecto o una referencia de ensamblado en el Explorador de soluciones, pueden mostrarse otras propiedades en la ventana Propiedades, según el tipo de archivo.  
  
### <a name="culture"></a>Referencia cultural  
 Muestra el idioma asociado a la referencia.  
  
### <a name="file-type"></a>Tipo de archivo  
 Muestra el tipo de archivo de la referencia.  
  
### <a name="file-version"></a>Versión de archivo  
 Muestra la versión de archivo de la referencia.  
  
### <a name="identity"></a>identidad  
 Muestra la identidad de la referencia que se usa en el proyecto, que se almacena en el archivo del proyecto.  
  
### <a name="package"></a>Package  
 Muestra el nombre del manifiesto de paquete asociado con la referencia.  
  
### <a name="resolved-path"></a>Ruta de acceso resuelta  
 Muestra la ruta de acceso a la referencia que se usa en el proyecto.  
  
### <a name="sdk-path"></a>Ruta de acceso del SDK  
 Muestra la ruta de acceso del archivo SDK al que se hace referencia.  
  
### <a name="uri"></a>URI  
 Muestra el URI que debe incluirse en los archivos del proyecto HTML o JavaScript para incluir el archivo como un archivo de origen.  
  
### <a name="version"></a>Versión  
 Muestra la versión de la referencia.  
  
## <a name="see-also"></a>Vea también  
 [NIB: Propiedades del proyecto (Visual Studio)](http://msdn.microsoft.com/en-us/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)



