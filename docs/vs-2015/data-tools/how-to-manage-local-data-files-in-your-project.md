---
title: 'Cómo: administrar archivos de datos locales en el proyecto | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.data.LocalConnectionConverter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- mdf files
- local data
- .mdb files
- .mdf files
- data [Visual Studio], local
- mdb files
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 16e2d38dda97bd8a7f130254b2f23be9f17e0ac4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271380"
---
# <a name="how-to-manage-local-data-files-in-your-project"></a>Cómo: Administrar archivos de datos locales en los proyectos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un archivo de base de datos local puede incluirse como un archivo en un proyecto. La primera vez que se conecte a un archivo de base de datos local, puede elegir crear una copia en el proyecto o conectarse al archivo existente en su ubicación actual. Si se conecta al archivo existente, se deja en su ubicación original. Si elige copiar el archivo en el proyecto, Visual Studio crea una copia de ella, lo agrega al proyecto y modifica la conexión para que apunte a la copia. También se puede modificar otras conexiones, como las de explorador de servidores.  
  
 La configuración predeterminada de la propiedad depende del tipo de archivo de base de datos que está usando. El comportamiento de la **Copy to Output Directory** propiedad no es aplicable a proyectos Web o C++.  
  
 Durante el desarrollo, puede ver los efectos del código en la base de datos sin realizar esos cambios permanentes. Puede hacerlo mediante la configuración de la **Copy to Output Directory** propiedad del archivo en true. Cada vez que el proyecto se compila o se presione F5, el archivo se copia en la carpeta bin y se realizan cambios en ese archivo, no en el archivo en la carpeta raíz del proyecto. El archivo de base de datos en la carpeta raíz del proyecto se cambia únicamente cuando se edición el esquema de base de datos o los datos mediante el uso de **Explorador de servidores**, **Database Explorer** u otra ventana de herramienta.  
  
 En la tabla siguiente se describe la configuración de la **Copy to Output Directory** propiedad.  
  
|Parámetro|Comportamiento|  
|-------------|--------------|  
|**Copiar si es posterior** (valor predeterminado para los archivos .sdf)|El archivo de base de datos se copia desde el directorio de proyecto para el **bin** directorio la primera vez que se compila el proyecto. Cada vez subsiguiente que se compile el proyecto, el **fecha de modificación** se compara la propiedad de los archivos. Si el archivo en la carpeta del proyecto es más reciente, se copia en el **bin** carpeta, reemplace el archivo que contenga. Si el archivo en el **bin** carpeta es más reciente, se copia ningún archivo. Esta configuración guarda los cambios realizados en los datos durante el tiempo de ejecución, lo que significa que cada vez que ejecute la aplicación y guarda los cambios en los datos, esos cambios serán visibles la próxima vez que ejecute la aplicación. **Precaución:** no se recomienda esta opción para los archivos .mdb o .mdf. Puede cambiar el archivo de base de datos incluso cuando no se realizan cambios en los datos. Simplemente abrir una conexión en un archivo de datos (por ejemplo, expandiendo el **tablas** nodo **Explorador de servidores**) puede marcarlo como más reciente.|  
|**Copiar siempre** (valor predeterminado para los archivos .mdf y .mdb)|El archivo de base de datos se copia desde el directorio del proyecto en el directorio /bin cada vez que compila la aplicación. Por lo tanto, si compila la aplicación y guarde los cambios en el archivo en el directorio/bin, esos cambios se sobrescriben la próxima vez que se copia el archivo original en el directorio/bin.|  
|**No copiar**|El archivo nunca se copia ni se sobrescribe el sistema del proyecto. Si usa esta configuración, manualmente debe copiar el archivo del directorio de proyecto en el directorio de salida.|  
  
## <a name="procedure"></a>Procedimiento  
  
#### <a name="to-respond-to-the-local-database-file-dialog-box"></a>Para responder al cuadro de diálogo de archivo de base de datos Local  
  
-   Haga clic en **Sí** si desea que Visual Studio copie el archivo de base de datos en el proyecto y modificar la conexión para que apunte a la copia en el proyecto. Para obtener más información sobre cómo trabajar con archivos de base de datos en el proyecto, vea [Local Data Overview](../data-tools/local-data-overview.md).  
  
-   Haga clic en **n** si no desea que Visual Studio copie el archivo de base de datos en el proyecto. En su lugar, los puntos de conexión en el archivo en la ubicación original y el archivo de base de datos no se agrega como un archivo al proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Conectarse a datos en un archivo de base de datos Local (formularios Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Conectar a los datos en una base de datos de Access (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)