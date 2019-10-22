---
title: El proceso de transformación de plantillas de texto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7322724b2118cb8b844262696a6e7cbd91a74e9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658505"
---
# <a name="the-text-template-transformation-process"></a>El proceso de transformación de las plantillas de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El proceso de transformación de plantillas de texto toma un archivo de plantilla de texto como entrada y genera un nuevo archivo de texto como salida. Por ejemplo, puede usar plantillas de texto para generar Visual Basic o C# código, o puede generar un informe HTML.

 Hay tres componentes que forman parte de este proceso: el motor, el host y los procesadores de directivas. El motor controla el proceso; interactúa con el host y el procesador de directivas para generar el archivo de salida. El host proporciona cualquier interacción con el entorno, como buscar archivos y ensamblados. El procesador de directivas agrega funcionalidad, como leer datos de un archivo XML o de una base de datos.

 El proceso de transformación de plantillas de texto se realiza en dos pasos. En primer lugar, el motor crea una clase temporal, que se conoce como la clase de transformación generada. Esta clase contiene el código generado por las directivas y los bloques de control. Después, el motor compila y ejecuta la clase de transformación generada para generar el archivo de salida.

## <a name="components"></a>Componentes

|Componente|Descripción|Personalizable (sí/no)|
|---------------|-----------------|------------------------------|
|Motor|El componente del motor controla el proceso de transformación de plantillas de texto|No.|
|administrador de flujos de trabajo|El host es la interfaz entre el motor y el entorno del usuario. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] es un host del proceso de transformación de texto.|Sí. Puede escribir un host personalizado.|
|Procesadores de directivas|Los procesadores de directivas son clases que controlan directivas en plantillas de texto. Puede utilizar directivas para proporcionar datos a una plantilla de texto desde un origen de entrada.|Sí. Puede escribir procesadores de directivas personalizados.|

## <a name="the-engine"></a>Motor de
 El motor recibe la plantilla como una cadena del host, que controla todos los archivos que se usan en el proceso de transformación. A continuación, el motor pide al host que busque cualquier procesador de directivas personalizado y otros aspectos del entorno. A continuación, el motor compila y ejecuta la clase de transformación generada. El motor devuelve el texto generado al host, que normalmente guarda el texto en un archivo.

## <a name="the-host"></a>El host
 El host es responsable de todo lo relacionado con el entorno fuera del proceso de transformación, incluido lo siguiente:

- Buscar archivos binarios y de texto solicitados por el motor o un procesador de directivas. El host puede buscar en los directorios y en la caché global de ensamblados para ubicar los ensamblados. El host puede localizar el código de procesador de directivas personalizado para el motor. El host también puede buscar y leer archivos de texto y devolver su contenido como cadenas.

- Proporcionar listas de los ensamblados y espacios de nombres estándar que usa el motor para crear la clase de transformación generada.

- Proporcionar el dominio de aplicación que se utiliza cuando el motor compila y ejecuta la clase de transformación generada. Se usa un dominio de aplicación independiente para proteger la aplicación host frente a errores en el código de plantilla.

- Escribir el archivo de salida generado.

- Establecer la extensión predeterminada para el archivo de salida generado.

- Control de errores de transformación de plantilla de texto. Por ejemplo, el host puede mostrar los errores en la interfaz de usuario o escribirlos en un archivo. (En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], los errores se muestran en la ventana de mensajes de error).

- Proporcionar un valor de parámetro necesario si un usuario ha llamado a una directiva sin proporcionar un valor. El procesador de directivas puede especificar el nombre de la Directiva y el parámetro, y pedir al host que proporcione un valor predeterminado si tiene uno.

## <a name="directives-and-directive-processors"></a>Directivas y procesadores de directivas
 Una directiva es un comando de la plantilla de texto. Proporciona parámetros para el proceso de generación. Normalmente, las directivas definen el origen y el tipo del modelo u otra entrada, y la extensión de nombre de archivo del archivo de salida.

 Un procesador de directivas puede procesar una o más directivas. Al transformar una plantilla, debe haber instalado un procesador de directivas que pueda tratar con las directivas de la plantilla.

 Las directivas funcionan agregando código en la clase de transformación generada. Se llama a las directivas desde una plantilla de texto y el motor procesa todas las llamadas a directivas cuando crea la clase de transformación generada. Después de llamar a una directiva correctamente, el resto del código que se escribe en la plantilla de texto puede basarse en la funcionalidad que proporciona la Directiva. Por ejemplo, puede hacer la siguiente llamada a la Directiva `import` en la plantilla:

 `<#@ import namespace="System.Text" #>`

 El procesador de directivas estándar lo convierte en una instrucción `using` en la clase de transformación generada. Después, puede usar la clase `StringBuilder` en el resto del código de plantilla sin calificarla como `System.Text.StringBuilder`.
