---
title: El proceso de transformación de las plantillas de texto
description: Obtenga información sobre que el proceso de transformación de la plantilla de texto toma un archivo de plantilla de texto como entrada y genera un nuevo archivo de texto como salida.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8dc827039253c21effffcc82d70b4f66ff284738
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388599"
---
# <a name="the-text-template-transformation-process"></a>El proceso de transformación de las plantillas de texto
El proceso de transformación de plantilla de texto toma un archivo de plantilla de texto como entrada y genera un nuevo archivo de texto como salida. Por ejemplo, puede usar plantillas de texto para generar Visual Basic código de C#, o bien puede generar un informe HTML.

 En este proceso participan tres componentes: el motor, el host y los procesadores de directivas. El motor controla el proceso; interactúa con el host y el procesador de directivas para generar el archivo de salida. El host proporciona cualquier interacción con el entorno, como buscar archivos y ensamblados. El procesador de directivas agrega funcionalidad, como leer datos de un archivo XML o una base de datos.

 El proceso de transformación de la plantilla de texto se realiza en dos pasos. En primer lugar, el motor crea una clase temporal, que se conoce como clase de transformación generada. Esta clase contiene el código generado por las directivas y los bloques de control. Después, el motor compila y ejecuta la clase de transformación generada para generar el archivo de salida.

## <a name="components"></a>Componentes

|Componente|Descripción|Personalizable (Sí/No)|
|-|-|-|
|Motor|El componente del motor controla el proceso de transformación de la plantilla de texto|No.|
|administrador de flujos de trabajo|El host es la interfaz entre el motor y el entorno de usuario. Visual Studio es un host del proceso de transformación de texto.|Sí. Puede escribir un host personalizado.|
|Procesadores de directivas|Los procesadores de directivas son clases que controlan directivas en plantillas de texto. Puede usar directivas para proporcionar datos a una plantilla de texto desde un origen de entrada.|Sí. Puede escribir procesadores de directivas personalizadas|

## <a name="the-engine"></a>El motor
 El motor recibe la plantilla como una cadena del host, que controla todos los archivos que se usan en el proceso de transformación. A continuación, el motor solicita al host que busque los procesadores de directivas personalizados y otros aspectos del entorno. A continuación, el motor compila y ejecuta la clase de transformación generada. El motor devuelve el texto generado al host, que normalmente guarda el texto en un archivo.

## <a name="the-host"></a>El host
 El host es responsable de todo lo relacionado con el entorno fuera del proceso de transformación, incluido lo siguiente:

- Buscar archivos binarios y de texto solicitados por el motor o un procesador de directivas. El host puede buscar directorios y la caché global de ensamblados para buscar ensamblados. El host puede buscar código de procesador de directivas personalizado para el motor. El host también puede buscar y leer archivos de texto y devolver su contenido como cadenas.

- Proporcionar listas de ensamblados estándar y espacios de nombres utilizados por el motor para crear la clase de transformación generada.

- Proporcionar el dominio de aplicación que se usa cuando el motor compila y ejecuta la clase de transformación generada. Se usa un dominio de aplicación independiente para proteger la aplicación host de errores en el código de plantilla.

- Escribir el archivo de salida generado.

- Establecer la extensión predeterminada para el archivo de salida generado.

- Control de errores de transformación de plantilla de texto. Por ejemplo, el host puede mostrar los errores en la interfaz de usuario o escribirlos en un archivo. (En Visual Studio, los errores se muestran en la ventana Mensaje de error).

- Proporcionar un valor de parámetro necesario si un usuario ha llamado a una directiva sin proporcionar un valor. El procesador de directivas puede especificar el nombre de la directiva y el parámetro y pedir al host que proporcione un valor predeterminado si tiene uno.

## <a name="directives-and-directive-processors"></a>Directivas y procesadores de directivas
 Una directiva es un comando de la plantilla de texto. Proporciona parámetros para el proceso de generación. Normalmente, las directivas definen el origen y el tipo del modelo u otra entrada, y la extensión de nombre de archivo del archivo de salida.

 Un procesador de directivas puede procesar una o varias directivas. Al transformar una plantilla, debe haber instalado un procesador de directivas que pueda tratar con las directivas de la plantilla.

 Las directivas funcionan agregando código en la clase de transformación generada. Llama a directivas desde una plantilla de texto y el motor procesa todas las llamadas de directiva cuando crea la clase de transformación generada. Después de llamar a una directiva correctamente, el resto del código que escribe en la plantilla de texto puede basarse en la funcionalidad que proporciona la directiva. Por ejemplo, puede realizar la siguiente llamada a la `import` directiva en la plantilla:

 `<#@ import namespace="System.Text" #>`

 El procesador de directivas estándar convierte esto en una `using` instrucción de la clase de transformación generada. A continuación, puede `StringBuilder` usar la clase en el resto del código de plantilla sin calificarla como `System.Text.StringBuilder` .
