---
title: El proceso de transformación de plantillas de texto | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0f92b4053006aa5da3c28d9330b372466f84d0fd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113994"
---
# <a name="the-text-template-transformation-process"></a>El proceso de transformación de las plantillas de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El proceso de transformación de plantillas de texto toma un archivo de plantilla de texto como entrada y genera un nuevo archivo de texto como salida. Por ejemplo, puede usar las plantillas de texto para generar el código de Visual Basic o C# o puede generar un informe HTML.  
  
 Tres componentes forman parte de este proceso: el motor, el host y los procesadores de directivas. El motor controla el proceso; interactúa con el host y el procesador de directivas para generar el archivo de salida. El host proporciona la interacción con el entorno, como buscar archivos y ensamblados. El procesador de directivas agrega funcionalidad, como leer datos desde un archivo XML o una base de datos.  
  
 El proceso de transformación de plantillas de texto se realiza en dos pasos. En primer lugar, el motor crea una clase temporal, que se conoce como la clase de transformación generada. Esta clase contiene el código generado por las directivas y los bloques de control. Después de eso, el motor se compila y ejecuta la clase de transformación generada para generar el archivo de salida.  
  
## <a name="components"></a>Componentes  
  
|Componente|Descripción|Puede personalizar (Sí/No)|  
|---------------|-----------------|------------------------------|  
|Motor de|El componente del motor controla el proceso de transformación de plantillas de texto|No.|  
|administrador de flujos de trabajo|El host es la interfaz entre el motor y el entorno del usuario. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] es un host del proceso de transformación de texto.|Sí. Puede escribir un host personalizado.|  
|Procesadores de directivas|Procesadores de directivas son clases que controlan las directivas en plantillas de texto. Puede usar directivas para proporcionar datos a una plantilla de texto desde un origen de entrada.|Sí. Puede escribir procesadores de directivas personalizadas|  
  
## <a name="the-engine"></a>El motor de  
 El motor recibe la plantilla como una cadena desde el host, que controla todos los archivos que se usan en el proceso de transformación. El motor de pregunta, a continuación, el host para localizar los procesadores de directivas personalizadas y otros aspectos del entorno. El motor, a continuación, compila y ejecuta la clase de transformación generada. El motor devuelve el texto generado para el host, que normalmente se guarda el texto en un archivo.  
  
## <a name="the-host"></a>El host  
 El host es responsable de todo lo que se relaciona con el entorno fuera del proceso de transformación, incluidos los siguientes:  
  
- Buscar archivos de texto y binarios solicitados por el motor o un procesador de directivas. El host puede buscar los directorios y la caché global de ensamblados para buscar ensamblados. El host puede localizar el código de procesador de directivas personalizadas para el motor. El host también puede buscar y leer archivos de texto y devolver su contenido como cadenas.  
  
- Proporcionar listas de ensamblados estándar y espacios de nombres utilizados por el motor para crear la clase de transformación generada.  
  
- Proporcionar el dominio de aplicación que se usa cuando el motor se compila y ejecuta la clase de transformación generada. Se usa un dominio de aplicación independiente con el fin de proteger la aplicación host de los errores en el código de plantilla.  
  
- Escribir el archivo de salida generado.  
  
- Establecer la extensión predeterminada del archivo de salida generado.  
  
- Control de errores de transformación de plantilla de texto. Por ejemplo, el host puede mostrar los errores en la interfaz de usuario o escribirlos en un archivo. (En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], los errores aparecen en la ventana de mensaje de Error.)  
  
- Al proporcionar un valor de parámetro necesario si un usuario ha llamado a una directiva sin proporcionar un valor. El procesador de directivas puede especificar el nombre de la directiva y el parámetro y pedir al host proporcionar un valor predeterminado si lo tiene.  
  
## <a name="directives-and-directive-processors"></a>Las directivas y los procesadores de directivas  
 Una directiva es un comando en la plantilla de texto. Proporciona los parámetros para el proceso de generación. Normalmente, las directivas definen el origen y el tipo del modelo u otra entrada y la extensión de nombre de archivo del archivo de salida.  
  
 Un procesador de directivas puede procesar uno o más directivas. Transformar una plantilla, debe tener instalados un procesador de directivas que puede tratar con las directivas en la plantilla.  
  
 Las directivas funcionan agregando código en la clase de transformación generada. Llamar a las directivas desde una plantilla de texto y el motor procesa todas las llamadas de la directiva cuando crea la clase de transformación generada. Después de llamar correctamente a una directiva, el resto del código que se escribe en la plantilla de texto puede basarse en la funcionalidad que proporciona la directiva. Por ejemplo, puede realizar la llamada siguiente a la `import` la directiva en la plantilla:  
  
 `<#@ import namespace="System.Text" #>`  
  
 El procesador de directivas estándar convierte esto a un `using` instrucción en la clase de transformación generada. A continuación, puede usar el `StringBuilder` clase en el resto del código de plantilla sin calificar como `System.Text.StringBuilder`.
