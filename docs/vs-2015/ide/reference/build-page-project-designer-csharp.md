---
title: Compilar (Página, Diseñador de proyectos) (C#) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a377db0ac82b672d053e59c621714945fa9b515c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837189"
---
# <a name="build-page-project-designer-c"></a>Compilar (Página, Diseñador de proyectos) (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Use la página **Compilar** del **Diseñador de proyectos** para especificar las propiedades de configuración de compilación del proyecto. Esta página se aplica solo a proyectos de [!INCLUDE[csprcs](../../includes/csprcs-md.md)].  
  
 Para obtener acceso a la página **Compilar**, seleccione un nodo de proyecto (no el nodo **Solución**) en el **Explorador de soluciones**. Después, pulse **Proyecto**, **Propiedades** en la barra de menús. Cuando se muestre el Diseñador de proyectos, haga clic en la pestaña **Compilar**.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="configuration-and-platform"></a>Configuración y plataforma  
 Las siguientes opciones le permiten seleccionar la configuración y la plataforma que se mostrarán o modificarán.  
  
> [!NOTE]
>  Con las configuraciones de compilación simplificadas, el sistema del proyecto determina si se debe compilar una versión de lanzamiento o depuración. Por tanto, estas opciones no se muestran. Para obtener más información, consulte [Configuraciones Debug y Release](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Configuración**  
 Especifica qué opciones de configuración se mostrarán o modificarán. Los valores pueden ser **(Depurar) activa** (es el valor predeterminado), **Depuración**, **Lanzamiento** o **Todas las configuraciones**.  
  
 **Plataforma**  
 Especifica qué configuración de plataforma se mostrará o modificará. La configuración predeterminada es **(Cualquier CPU) activa**. Puede cambiar la plataforma activa mediante el **Administrador de configuración**. Para obtener más información, consulte [Cómo: Crear y editar configuraciones](../../ide/how-to-create-and-edit-configurations.md).  
  
## <a name="general"></a>General  
 Las opciones siguientes le permiten configurar varias opciones del compilador de C#.  
  
 **Símbolos de compilación condicional**  
 Especifica símbolos con los que realizar la compilación condicional. Separe los símbolos con un punto y coma (";"). Para obtener más información, consulte [/define (Opciones del compilador de C#)](http://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).  
  
 **Definir constante DEBUG**  
 Define DEBUG como un símbolo en todos los archivos de código fuente de la aplicación. Seleccionar esta opción equivale a usar la opción de línea de comandos `/define:DEBUG`.  
  
 **Definir constante TRACE**  
 Define TRACE como un símbolo en todos los archivos de código fuente de la aplicación. Seleccionar esta opción equivale a usar la opción de línea de comandos `/define:TRACE`.  
  
 **CPU de destino**  
 Especifica el procesador que será el destino del archivo de salida. Elija **x86** para cualquier procesador compatible con Intel de 32 bits; elija **x64** para cualquier procesador compatible con Intel de 64 bits; elija **ARM** para procesadores ARM; o elija **Cualquier CPU** para especificar que se aceptan todos los procesadores. **Cualquier CPU** es el valor predeterminado para los proyectos, ya que permite que la aplicación se ejecute en la gran mayoría del hardware.  
  
 Para obtener más información, consulte [/platform (Opciones del compilador de C#)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).  
  
 **Preferencia de 32 bits**  
 Si está seleccionada la casilla **Preferencia de 32 bits**, la aplicación se ejecuta como una aplicación de 32 bits en versiones de 32 bits y 64 bits de Windows. Si la casilla está desactivada, la aplicación se ejecutará como una aplicación de 32 bits en versiones de 32 bits de Windows y como una aplicación de 64 bits en versiones de 64 bits de Windows.  
  
 Si ejecuta una aplicación como una aplicación de 64 bits, el tamaño del puntero es el doble y se pueden producir problemas de compatibilidad con otras bibliotecas que son exclusivamente de 32 bits. Es útil ejecutar una aplicación de 64 bits solo si necesita más de 4 GB de memoria o si las instrucciones de 64 bits proporcionan una mejora considerable del rendimiento.  
  
 Esta casilla solo está disponible si se cumplen todas las condiciones siguientes:  
  
- En **Compilar página**, la lista **Destino de la plataforma** está establecida en **Cualquier CPU**.  
  
- En la **Página de aplicación**, la lista **Tipo de salida** especifica que el proyecto es una aplicación.  
  
- En la **Página de aplicación**, la lista **Marco de trabajo de destino** especifica .NET Framework 4.5.  
  
  **Permitir código no seguro**  
  Permite la compilación de código en el que se usa la palabra clave [unsafe](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0). Para obtener más información, consulte [/unsafe (Opciones del compilador de C#)](http://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).  
  
  **Optimizar código**  
  Habilite o deshabilite las optimizaciones realizadas por el compilador para que el archivo de salida sea menor, más rápido y más eficaz. Para obtener más información, consulte [/optimize (Opciones del compilador de C#)](http://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).  
  
## <a name="errors-and-warnings"></a>Errores y advertencias  
 Las siguientes opciones se usan para configurar las opciones de advertencia y error para el proceso de compilación.  
  
 **Nivel de advertencia**  
 Especifica el nivel que se debe mostrar para las advertencias del compilador. Para obtener más información, consulte [/warn (Opciones del compilador de C#)](http://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).  
  
 **Suprimir advertencias**  
 Bloquea la capacidad del compilador de generar una o varias advertencias. Separe varios números de advertencia con una coma o un punto y coma. Para obtener más información, consulte [/nowarn (Opciones del compilador de C#)](http://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).  
  
## <a name="treat-warnings-as-errors"></a>Tratar advertencias como errores  
 Las siguientes opciones se usan para especificar qué advertencias se tratan como errores. Seleccione una de las siguientes opciones para indicar en qué condiciones se devolverá un error cuando la compilación encuentra una advertencia. Para obtener más información, consulte [/warnaserror (Opciones del compilador de C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).  
  
 **Ninguno**  
 No trata ninguna advertencia como error.  
  
 **Advertencias específicas**  
 Trata las advertencias especificadas como errores. Separe varios números de advertencia con una coma o un punto y coma.  
  
 **All**  
 Trata todas las advertencias como errores.  
  
## <a name="output"></a>Salida  
 Las siguientes opciones se usan para configurar las opciones de salida para el proceso de compilación.  
  
 **Ruta de acceso de salida**  
 Especifica la ubicación de los archivos de salida para la configuración de este proyecto. Escriba la ruta de acceso de salida de la compilación en este cuadro, o elija el botón **Examinar** para especificar una ruta de acceso. Tenga en cuenta que la ruta de acceso es relativa; si especifica una ruta de acceso absoluta, se guardará como relativa. La ruta de acceso predeterminada es bin\Debug o bin\Release\\. Para obtener más información, consulte [Configuraciones Debug y Release](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 Con las configuraciones de compilación simplificadas, el sistema del proyecto determina si se debe compilar una versión de lanzamiento o depuración. El comando **Compilar** del menú **Depuración** (F5) colocará la compilación en la ubicación de depuración independientemente de la **Ruta de acceso de salida** que especifique. En cambio, el comando **Compilar** del menú **Compilar** la coloca en la ubicación que especifique. Para obtener más información, consulte [Configuraciones Debug y Release](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Archivo de documentación XML**  
 Especifica el nombre de un archivo en el que se procesarán comentarios sobre documentación. Para obtener más información, consulte [/doc (Opciones del compilador de C#)](http://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).  
  
 **Registrar para interoperabilidad COM**  
 Indica que la aplicación administrada expondrá un objeto COM (un contenedor CCW) que permite a un objeto COM interactuar con la aplicación administrada. La propiedad **Tipo de salida** de la [página Aplicación](../../ide/reference/application-page-project-designer-visual-basic.md) del **Diseñador de proyectos** de esta aplicación debe establecerse en **Biblioteca de clases** para que la propiedad **Registrar para interoperabilidad COM** esté disponible. Para ver una clase de ejemplo que puede incluir en la aplicación de [!INCLUDE[csprcs](../../includes/csprcs-md.md)] y exponer como un objeto COM, consulte [Clase COM de ejemplo](http://msdn.microsoft.com/library/6504dea9-ad1c-4993-a794-830fec5270af).  
  
 **Generar ensamblados de serialización**  
 Especifica si el compilador usará la herramienta Generador de serializador XML (Sgen.exe) para crear ensamblados de serialización XML. Los ensamblados de serialización pueden mejorar el rendimiento de inicio de <xref:System.Xml.Serialization.XmlSerializer> si ha usado esa clase para serializar los tipos en el código. De manera predeterminada, esta opción se establece en **Automático**, que especifica que los ensamblados de serialización se generan solo si ha usado <xref:System.Xml.Serialization.XmlSerializer> para codificar los tipos del código en XML. **Desactivado** especifica que los ensamblados de serialización no se generan nunca, independientemente de si el código usa <xref:System.Xml.Serialization.XmlSerializer>. **Activado** especifica que siempre se generan ensamblados de serialización. Los ensamblados de serialización se denominan `TypeName`.XmlSerializers.dll. Para obtener más información, consulte [Herramienta Generador de serializador XML (Sgen.exe)](http://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
 **Avanzadas**  
 Haga clic para mostrar el cuadro de diálogo [Configuración de compilación avanzada (Cuadro de diálogo, C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de propiedades del proyecto](../../ide/reference/project-properties-reference.md)   
 [Opciones del compilador de C#](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)



