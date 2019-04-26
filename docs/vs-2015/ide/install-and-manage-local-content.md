---
title: Instalar y administrar el contenido local | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer 2.0]
- updating local content [Help Viewer 2.0]
- Help Viewer 2.0, content installation source
- Help Viewer 2.0, updating local content
- Help Viewer 2.0, changing content installation source
- installing local content [Help Viewer 2.0]
- content installation source [Help Viewer 2.0]
- downloading content [Help Viewer 2.0]
- removing local content [Help Viewer 2.0]
- Help Viewer 2.0, removing local content
- Help Viewer 2.0, installing local content
- Help Viewer 2.0, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a5ad9c363a590ef692bdcd1d8c00727d55113b97
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412356"
---
# <a name="install-and-manage-local-content"></a>Instalar y administrar el contenido local
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con el Visor de Ayuda de Microsoft, puede agregar, quitar, actualizar y mover el contenido de Ayuda que se instala en el equipo para ajustarlo a sus necesidades de desarrollo de software.  
  
 Para administrar el contenido en el equipo local, debe iniciar sesión con una cuenta que tenga permisos administrativos. Además, es posible que no pueda administrar contenido local si trabaja en un entorno empresarial, ya que los administradores del sistema podrían tomar esas decisiones por su organización. Para obtener más información, vea la [Guía del administrador del Visor de Ayuda](../ide/help-viewer-administrator-guide.md).  
  
## <a name="changing-the-content-installation-source"></a>Cambiar el origen de instalación del contenido  
 De forma predeterminada, el Visor de Ayuda instala contenido mediante el uso de un servicio en línea de Microsoft como el origen. En general, no debería cambiar el origen del contenido a menos que trabaje en un entorno empresarial para el que un administrador del sistema ya instaló contenido en otra ubicación.  
  
#### <a name="to-change-the-content-installation-source"></a>Para cambiar el origen de instalación del contenido  
  
1. En la pestaña **Administrar contenido**, pulse el botón de opción **Disco**.  
  
    > [!NOTE]
    > La opción **Disco** no estará disponible si el administrador impide modificar el origen de instalación del contenido. Para obtener más información, vea la [Guía del administrador del Visor de Ayuda](../ide/help-viewer-administrator-guide.md).  
  
2. Realice uno de estos pasos:  
  
    - Escriba la ruta de un archivo MSHA o la URL de un punto de conexión de servicio.  
  
    - Haga clic en el botón Examinar (**...**) para desplazarse hasta un archivo .msha.  
  
    - En la lista, seleccione la entrada que se usó más recientemente.  
  
## <a name="download-and-install-content-locally"></a>Descargar e instalar contenido localmente  
 Puede ver temas sin conexión a Internet si descarga e instala el contenido en el equipo local.  
  
> [!IMPORTANT]
> Para instalar contenido, debe iniciar sesión con una cuenta que tenga permisos administrativos.  
  
 Si se establece el IDE de Visual Studio en un idioma distinto del inglés, puede instalar contenido en inglés, el contenido localizado o ambos. En cambio, el contenido no aparecerá si instala solo la versión en inglés y la casilla **Incluir contenido en inglés en todas las pestañas de navegación y solicitudes de F1** en el cuadro de diálogo **Opciones del Visor** está desactivada.  
  
#### <a name="to-download-and-install-content"></a>Para descargar e instalar contenido  
  
1. Pulse la pestaña **Administrar contenido**.  
  
2. En la lista de contenido, pulse el vínculo **Agregar** junto al libro o libros que quiere descargar e instalar.  
  
     El libro se agrega a la lista **Cambios pendientes** y el tamaño estimado del libro o libros que ha especificado aparece debajo de esa lista. Dado que algunos libros comparten temas, el tamaño total de la descarga de varios libros podría ser menor que el resultado de la suma de los tamaños de todos los libros que especificó.  
  
3. Pulse el botón **Actualizar**.  
  
     El libro o libros que especificó se instalan junto con todas las actualizaciones de los libros que ya existen en el equipo. Los tiempos de instalación varían, pero puede ver el progreso en la barra de estado.  
  
## <a name="removing-local-content"></a>Quitar el contenido local  
 Puede ahorrar espacio en disco mediante la eliminación de contenido no deseado de su equipo.  
  
> [!IMPORTANT]
> Debe tener permisos administrativos para quitar contenido.  
  
 No aparecerá ningún contenido si el IDE de Visual Studio está en un idioma distinto del inglés, quita el contenido localizado y la casilla **Incluir contenido en inglés en todas las pestañas de navegación y las solicitudes de F1** del cuadro de diálogo **Opciones del Visor** está desactivada.  
  
#### <a name="to-remove-content"></a>Para quitar contenido  
  
1. Pulse la pestaña **Administrar contenido**.  
  
2. En la lista de contenido, pulse el vínculo **Quitar** junto al libro o libros que quiere quitar.  
  
     El libro se agrega a la lista de **Cambios pendientes**.  
  
3. Pulse el botón **Actualizar**.  
  
     El libro o libros que especificó se quitan de su equipo.  
  
## <a name="updating-local-content"></a>Actualizar el contenido local  
 La barra de estado indica cuándo hay disponibles actualizaciones para el contenido instalado.  
  
> [!IMPORTANT]
> Si quiere que el Visor de Ayuda busque automáticamente actualizaciones en línea, debe abrir el cuadro de diálogo **Opciones del Visor** y, después, seleccione la casilla **Conectarse para comprobar actualizaciones de contenido**.  
  
#### <a name="to-update-local-content"></a>Para actualizar el contenido local  
  
- En la esquina inferior derecha de la barra de estado, pulse el vínculo **Haga clic aquí para descargar ahora**.  
  
  Los tiempos de actualización pueden variar, pero puede ver el progreso de actualización en la barra de estado.  
  
## <a name="moving-local-content"></a>Mover el contenido local  
 Puede ahorrar espacio en disco moviendo contenido instalado en el equipo local a un recurso compartido de red o a otra partición en el equipo local.  
  
> [!IMPORTANT]
> Para mover el contenido, debe iniciar sesión con una cuenta que tenga permisos administrativos.  
  
#### <a name="to-move-local-content"></a>Para mover contenido local  
  
1. En la pestaña **Administrar contenido**, pulse el botón **Mover** en **Ruta de acceso del almacén local**.  
  
     Se abre el cuadro de diálogo **Mover contenido**.  
  
2. En el cuadro de texto **Para**, escriba una ubicación diferente para el contenido y, después, pulse el botón **Aceptar**.  
  
3. Pulse el botón **Cerrar** cuando el contenido se termine de mover.  
  
## <a name="see-also"></a>Vea también  
 [Visor de Ayuda de Microsoft](../ide/microsoft-help-viewer.md)
