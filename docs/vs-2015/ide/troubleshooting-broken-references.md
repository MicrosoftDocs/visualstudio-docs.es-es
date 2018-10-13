---
title: Solucionar problemas de referencias rotas | Microsoft Docs
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
- Visual C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
ms.assetid: 00a9ade9-652e-40de-8ada-85f63cd183ee
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 08cf57bb90ba85df8a818da92cfd5615c62c3468
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292947"
---
# <a name="troubleshooting-broken-references"></a>Troubleshooting Broken References
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si la aplicación intenta usar una referencia rota, se genera un error de excepción. La incapacidad de encontrar el componente al que se hace referencia es el desencadenador principal del error, pero hay varias situaciones en las que se puede considerar una referencia como rota. Estas instancias se muestran en la siguiente lista:  
  
-   La ruta de acceso de referencia del proyecto es incorrecta o está incompleta.  
  
-   Se ha eliminado el archivo al que se hace referencia.  
  
-   Se ha cambiado el nombre del archivo al que se hace referencia.  
  
-   Se ha producido un error en la conexión de red o en la autenticación.  
  
-   Se hace referencia a un componente COM que no está instalado en el equipo.  
  
 A continuación se ofrecen soluciones a estos problemas.  
  
> [!NOTE]
>  Se hace referencia a los archivos de los ensamblados mediante rutas de acceso absolutas en el archivo del proyecto. Por tanto, es posible que a los usuarios que trabajan en un entorno de varios desarrolladores les falte un ensamblado al que se hace referencia en su entorno local. Para evitar estos errores, en estos casos es mejor agregar referencias entre proyectos. Para obtener más información, consulte [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) y [Programar con ensamblados](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6).  
  
## <a name="reference-path-is-incorrect"></a>La ruta de acceso de referencia es incorrecta  
 Si los proyectos se comparten en equipos diferentes, es posible que no se encuentren algunas referencias cuando un componente se encuentra en un directorio diferente en cada equipo. Las referencias se almacenan con el nombre del archivo de componente (por ejemplo, MyComponent). Cuando se agrega una referencia a un proyecto, la ubicación de la carpeta del archivo de componente (por ejemplo, C:\MyComponents\\) se anexa a la propiedad del proyecto **ReferencePath**.  
  
 Cuando se abre el proyecto, intenta encontrar estos archivos de componente a los que se hace referencia mediante una búsqueda en los directorios de la ruta de acceso de referencia. Si el proyecto se abre en un equipo que almacena el componente en otro directorio, por ejemplo, D:\MyComponents\\, no se puede encontrar la referencia y aparece un error en la lista de tareas.  
  
 Para corregir este problema, puede eliminar la referencia rota y después reemplazarla mediante el cuadro de diálogo Agregar referencia. Otra solución es usar el elemento **Reference Path** (Ruta de acceso de referencia) en las páginas de propiedades del proyecto y modificar las carpetas de la lista para que apunten a las ubicaciones correctas. La propiedad **Reference Path** se guarda para cada usuario en cada equipo. Por tanto, si modifica la ruta de acceso de referencia, esto no afecta a otros usuarios del proyecto.  
  
> [!TIP]
>  Las referencias entre proyectos no tienen estos problemas. Por este motivo, úselas en lugar de las referencias de archivo, si es posible.  
  
#### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Para reparar una referencia de proyecto rota mediante la corrección de la ruta de acceso de referencia  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y haga clic en **Propiedades**.  
  
2.  Aparece el **Diseñador de proyectos**.  
  
3.  Si usa Visual Basic, seleccione la página **Referencias** y haga clic en el botón **Rutas de acceso de referencia**. En el cuadro de diálogo **Rutas de acceso de referencia**, escriba la ruta de acceso de la carpeta que contiene el elemento al que quiere hacer referencia en el campo **Carpeta** y luego haga clic en el botón **Agregar carpeta**.  
  
     O bien  
  
     Si usa Visual C#, seleccione la página **Rutas de acceso de referencia**. En el campo **Carpeta**, escriba la ruta de acceso de la carpeta que contiene el elemento al que quiere hacer referencia y luego haga clic en el botón **Agregar carpeta**.  
  
## <a name="referenced-file-has-been-deleted"></a>Se ha eliminado el archivo al que se hace referencia  
 Es posible que el archivo al que se hace referencia se haya eliminado y ya no exista en la unidad.  
  
#### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Para reparar una referencia de proyecto rota de un archivo que ya no existe en la unidad  
  
-   Elimine la referencia.  
  
-   Si la referencia existe en otra ubicación del equipo, léala desde esa ubicación.  
  
-   Para obtener más información, consulte [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="referenced-file-has-been-renamed"></a>Se ha cambiado el nombre del archivo al que se hace referencia  
 Es posible que se haya cambiado el nombre del archivo al que se hace referencia.  
  
#### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Para reparar una referencia rota de un archivo al que se le ha cambiado el nombre  
  
-   Elimine la referencia y después agregue una referencia al archivo al que se le ha cambiado el nombre.  
  
-   Si la referencia existe en otra ubicación del equipo, tiene que leerla desde esa ubicación. Para obtener más información, consulte [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="network-connection-or-authentication-has-failed"></a>Se ha producido un error en la conexión de red o en la autenticación  
 Puede haber varias causas por las que no se pueda tener acceso a los archivos, por ejemplo, una conexión de red o una autenticación incorrectas. Cada causa puede tener un único medio de recuperación; por ejemplo, es posible que tenga que ponerse en contacto con el administrador local para acceder a los recursos necesarios. No obstante, siempre hay la opción de eliminar la referencia y corregir el código en el que se usaba esa referencia. Para obtener más información, consulte [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="com-component-is-not-installed-on-computer"></a>No se ha instalado el componente COM en el equipo  
 Si un usuario ha agregado una referencia a un componente COM y un segundo usuario intenta ejecutar el código en un equipo que no tenga este componente instalado, el segundo usuario recibirá un error que indica que la referencia está rota. Si se instala el componente en el segundo equipo, se corregirá el error. Para obtener más información sobre cómo usar referencias a componentes COM en los proyectos, consulte [Interoperabilidad COM en aplicaciones .NET Framework](http://msdn.microsoft.com/library/f5a72143-c268-4dff-a019-974ad940e17d).  
  
## <a name="see-also"></a>Vea también  
 [Introducción al Diseñador de proyectos](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)   
 [Página Referencias, Diseñador de proyectos (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)   
 [Cómo: Agregar o quitar referencias con el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)



