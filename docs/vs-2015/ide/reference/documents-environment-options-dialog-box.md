---
title: Documentos, Entorno, Opciones (Cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
- VS.ToolsOptionsPag.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1cd368730ec4df91840984525bf0042963587e68
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444711"
---
# <a name="documents-environment-options-dialog-box"></a>Documentos, Entorno, Opciones (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use esta página del cuadro de diálogo **Opciones** para controlar la visualización de documentos en el entorno de desarrollo integrado (IDE) y administrar los cambios externos de los documentos y archivos. Puede tener acceso a este cuadro de diálogo haciendo clic en **Opciones** en el menú **Herramientas** y, después, seleccionar **Documentos** en el nodo **Entorno**. Si **Documentos** no aparece en la lista, en el cuadro de diálogo **Opciones**, seleccione **Mostrar todas las configuraciones**.  
  
> [!NOTE]
> Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Reusar la ventana de documento activa si se guardó**  
 Cuando está seleccionada, cierra su documento actual si se ha guardado y abre un nuevo documento en la misma ventana. Si el documento actual no se ha guardado, permanece abierto y el documento nuevo se abre en una ventana independiente. Cuando esta opción se desactiva, los documentos nuevos siempre se abren en ventanas independientes.  
  
 Si realiza operaciones de copiar y pegar varios documentos con poca frecuencia y quiere minimizar el número de documentos abiertos y ventanas en su área de trabajo, pruebe esta opción.  
  
 **Detectar si se modifica el archivo fuera del entorno**  
 Cuando esta opción está seleccionada, un mensaje le notifica inmediatamente los cambios en un archivo abierto que ha realizado un editor externo al IDE. Este mensaje le permite volver a cargar el archivo del almacenamiento.  
  
 **Cargar cambios automáticamente, si están guardados**  
 Cuando tiene la opción **Detectar si se modifica el archivo fuera del entorno** seleccionada y un archivo abierto en el IDE se cambia fuera de este, se genera un mensaje de advertencia de manera predeterminada. Si esta opción está habilitada, no aparece ninguna advertencia y el documento se vuelve a cargar en el IDE para recopilar los cambios externos.  
  
 **Permitir la edición de archivos de solo lectura; advertir al guardarlos**  
 Cuando esta opción está habilitada, puede abrir y editar un archivo de solo lectura. Cuando termine, debe usar el comando **Guardar como** para guardar el archivo con un nombre nuevo si quiere guardar un registro de sus cambios.  
  
 **Abrir archivo usando el directorio del documento activo actualmente**  
 Cuando está seleccionada, esta opción especifica que el cuadro de diálogo **Abrir archivo** muestra el directorio del documento activo. Cuando esta opción está desactivada, el cuadro de diálogo **Abrir archivo** muestra el último directorio que se ha usado para abrir un archivo.  
  
 **Comprobar que el fin de línea sea coherente al cargar**  
 Seleccione esta opción para que el editor analice los finales de línea en un archivo y muestre un cuadro de mensaje si se detectan incoherencias en el formato de los finales de línea.  
  
 **Mostrar una advertencia si la operación Deshacer global modifica archivos editados**  
 Seleccione esta opción para mostrar un cuadro de mensaje cuando el comando **Deshacer global** revertirá los cambios de refactorización que se han realizado en los archivos que también se han cambiado tras la operación de refactorización. Al devolver un archivo a su estado previo a la refactorización puede descartar los cambios posteriores que se han realizado en el archivo.  
  
 **Mostrar archivos varios en el Explorador de soluciones**  
 Seleccione esta opción para mostrar el nodo **Archivos varios** en el **Explorador de soluciones**. Los archivos varios son archivos que no están asociados a ninguna solución o proyecto, pero que pueden aparecer en el **Explorador de soluciones** por comodidad.  
  
> [!NOTE]
> Seleccione esta opción para habilitar el comando **Ver en el explorador** del menú **Archivo** para los documentos web que no están incluidos en la aplicación web activa.  
  
 **\<** *n* **> elementos guardados en el proyecto de archivos varios**  
 Especifica el número de archivos que se va a conservar en la carpeta **Archivos varios** del **Explorador de soluciones**. Estos archivos se muestran incluso si ya no están abiertos en un editor. Puede especificar cualquier número entero de 0 a 256. El número predeterminado es 0.  
  
 Por ejemplo, si establece esta opción en 5 y tiene 10 archivos varios abiertos, cuando cierre los 10 archivos, los primeros 5 se seguirán mostrando en la carpeta **Archivos varios**.  
  
 **Guardar documentos como Unicode cuando no se puedan guardar los datos en la página de códigos**  
 Seleccione esta opción para provocar que los archivos que contienen información no compatible con la página de códigos seleccionada se guarden como Unicode de manera predeterminada.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de entorno (Cuadro de diálogo)](../../ide/reference/environment-options-dialog-box.md)   
 [Archivos varios](../../ide/reference/miscellaneous-files.md)   
 [Buscar y reemplazar texto](../../ide/finding-and-replacing-text.md)
