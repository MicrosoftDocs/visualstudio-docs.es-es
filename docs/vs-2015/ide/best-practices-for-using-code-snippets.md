---
title: Procedimientos recomendados para usar fragmentos de código | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6c02abbef9a5a9022e5a887c5a9aa452143adb8b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241324"
---
# <a name="best-practices-for-using-code-snippets"></a>Procedimientos recomendados para usar fragmentos de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El código de un fragmento de código muestra solo la forma más sencilla de hacer algo. Para la mayoría de las aplicaciones, el código debe modificarse para adaptarlo a la aplicación.  
  
## <a name="handling-exceptions"></a>Controlar las excepciones  
 Normalmente, el fragmento de código Try... Catch bloquea catch y vuelve a iniciar todas las excepciones. Es posible que esta no sea la elección correcta para su proyecto. Para cada excepción, hay varias formas de responder. Para obtener ejemplos, consulte [Cómo: Controlar una excepción mediante Try y Catch (Guía de programación de C#)](http://msdn.microsoft.com/library/ca8e3773-980e-4767-8633-7408540e9818) y [Try...Catch...Finally (instrucción)](http://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b).  
  
## <a name="file-locations"></a>Ubicaciones de archivos  
 Al adaptar las ubicaciones de archivo a la aplicación, debe tener en cuenta lo siguiente:  
  
-   Encontrar una ubicación accesible. Es posible que los usuarios no tengan acceso a la carpeta Archivos de programa del equipo, por lo que puede que no sirva almacenar archivos con los archivos de aplicación.  
  
-   Encontrar una ubicación segura. Almacenar archivos en la carpeta raíz (C:\\) no es seguro. Para datos de aplicaciones, le recomendamos la carpeta \Application Data. Para los datos de los usuarios, la aplicación puede crear un archivo para cada usuario en la carpeta \Mis documentos.  
  
-   Usar un nombre de archivo válido. Puede usar los controles <xref:System.Windows.Forms.OpenFileDialog> y <xref:System.Windows.Forms.SaveFileDialog> para reducir la probabilidad de nombres de archivo no válidos. Tenga en cuenta que, entre el momento en que el usuario selecciona un archivo y el tiempo que el código manipula el archivo, se puede eliminar el archivo. Además, es posible que el usuario no tenga permisos para escribir en el archivo.  
  
## <a name="security"></a>Seguridad  
 El nivel de seguridad de un fragmento de código depende de dónde se usa en el código fuente y cómo se modifica una vez que está en el código. La lista siguiente contiene algunas de las áreas que deben tenerse en cuenta.  
  
-   Acceso de base de datos y archivo  
  
-   Seguridad de acceso del código  
  
-   Protección de recursos (como registros de eventos, Registro)  
  
-   Almacenamiento de secretos  
  
-   Comprobación de entradas  
  
-   Paso de datos a tecnologías de scripting  
  
 Para obtener más información, consulte [Proteger aplicaciones](../ide/securing-applications.md).  
  
## <a name="downloaded-code-snippets"></a>Fragmentos de código descargados  
 Los fragmentos de código de IntelliSense instalados por Visual Studio no constituyen por sí mismos un peligro para la seguridad. En cambio, pueden crear riesgos de seguridad en la aplicación. Los fragmentos de código descargados de Internet deben tratarse como cualquier otro contenido descargado: con extrema precaución.  
  
-   Descargue fragmentos solo de sitios de confianza y use software antivirus actualizado.  
  
-   Abra todos los archivos de fragmento de código descargados en el Bloc de notas o el editor XML de Visual Studio y examínelos detenidamente antes de instalarlos. Busque los siguientes problemas:  
  
    -   El fragmento de código podría dañar el sistema si lo ejecuta. Lea detenidamente el código fuente antes de ejecutarlo.  
  
    -   El bloque Dirección URL de la Ayuda del archivo de fragmento de código puede contener direcciones URL que ejecuten un archivo de script malintencionado o muestren un sitio web ofensivo.  
  
    -   El fragmento de código puede contener referencias que se agregan automáticamente al proyecto y es posible que se carguen desde cualquier lugar del sistema. Es posible que estas referencias se hayan descargado en el equipo desde el mismo sitio del que ha descargado el fragmento de código. El fragmento de código puede realizar una llamada a un método en la referencia que ejecuta código malintencionado. Para protegerse contra este tipo de ataque, revise los bloques Importaciones y Referencias del archivo de fragmentos.  
  
## <a name="see-also"></a>Vea también  
 [Fragmentos de código de IntelliSense de Visual Basic](http://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643)   
 [Proteger aplicaciones](../ide/securing-applications.md)   
 [Fragmentos de código](../ide/code-snippets.md)



