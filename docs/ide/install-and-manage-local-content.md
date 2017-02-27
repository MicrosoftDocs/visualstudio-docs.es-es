---
title: "Instalar y administrar el contenido local | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hv_manage"
helpviewer_keywords: 
  - "cambiar el origen de instalación del contenido [Visor de Ayuda 2.0]"
  - "origen de instalación del contenido [Visor de Ayuda 2.0]"
  - "descargar contenido [Visor de Ayuda 2.0]"
  - "Visor de Ayuda 2.0, cambiar el origen de instalación del contenido"
  - "Visor de Ayuda 2.0, origen de instalación del contenido"
  - "Visor de Ayuda 2.0, descargar el contenido"
  - "Visor de Ayuda 2.0, instalar el contenido local"
  - "Visor de Ayuda 2.0, quitar el contenido local"
  - "Visor de Ayuda 2.0, actualizar el contenido local"
  - "instalar el contenido local [Visor de Ayuda 2.0]"
  - "quitar el contenido local [Visor de Ayuda 2.0]"
  - "actualizar el contenido local [Visor de Ayuda 2.0]"
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Instalar y administrar el contenido local
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con el Visor de Ayuda de Microsoft, puede agregar, quitar, actualizar y mover el contenido de Ayuda que se instala en el equipo para ajustarlo a sus necesidades de desarrollo de software.  
  
 Para administrar el contenido en el equipo local, debe iniciar sesión con una cuenta que tenga permisos administrativos.  Además, es posible que no pueda administrar contenido local si trabaja en un entorno empresarial, ya que los administradores del sistema podrían tomar esas decisiones por su organización.  Para obtener más información, consulte la [Guía del administrador del Visor de Ayuda](../ide/help-viewer-administrator-guide.md).  
  
## Cambiar el origen de instalación del contenido  
 De forma predeterminada, el Visor de Ayuda instala contenido mediante el uso de un servicio en línea de Microsoft como el origen.  En general, no debería cambiar el origen del contenido a menos que trabaje en un entorno empresarial para el que un administrador del sistema ya instaló contenido en otra ubicación.  
  
#### Para cambiar el origen de instalación del contenido  
  
1.  En la pestaña **Administrar contenido**, elija el botón de la opción **Disco**.  
  
    > [!NOTE]
    >  La opción **Disco** no estará disponible si el administrador impide modificar el origen de instalación del contenido.  Para obtener más información, consulte la [Guía del administrador del Visor de Ayuda](../ide/help-viewer-administrator-guide.md).  
  
2.  Realice uno de estos pasos:  
  
    -   Escriba la ruta de un archivo MSHA o la URL de un extremo de servicio.  
  
    -   Elija el botón Examinar \(**...**\) para desplazarse hasta un archivo MSHA.  
  
    -   En la lista, seleccione la entrada que se usó más recientemente.  
  
## Descargar e instalar contenido localmente  
 Puede ver temas sin conexión a Internet si descarga e instala el contenido en el equipo local.  
  
> [!IMPORTANT]
>  Para instalar contenido, debe iniciar sesión con una cuenta que tenga permisos administrativos.  
  
 Si se establece el IDE de Visual Studio en un idioma distinto del inglés, puede instalar contenido en inglés, el contenido localizado o ambos.  Sin embargo, el contenido no aparecerá si instala solo la versión en inglés y la casilla **Incluir contenido en inglés en todas las pestañas de navegación y solicitudes de F1** en el cuadro de diálogo **Opciones del Visor** está desactivada.  
  
#### Para descargar e instalar contenido  
  
1.  Elija la pestaña **Administrar contenido**.  
  
2.  En la lista de contenido, elija el vínculo **Agregar** junto al libro o libros que desea descargar e instalar.  
  
     El libro se agrega a la lista **Cambios pendientes** y el tamaño estimado del libro o libros que especificó aparece debajo de esa lista.  Dado que algunos libros comparten temas, el tamaño total de la descarga de varios libros podría ser menor que el resultado de la suma de los tamaños de todos los libros que especificó.  
  
3.  Elija el botón de **Actualizar**.  
  
     El libro o libros que especificó se instalan junto con todas las actualizaciones de los libros que ya existen en el equipo.  Los tiempos de instalación varían, pero puede ver el progreso en la barra de estado.  
  
## Quitar el contenido local  
 Puede ahorrar espacio en disco mediante la eliminación de contenido no deseado de su equipo.  
  
> [!IMPORTANT]
>  Debe tener permisos administrativos para quitar contenido.  
  
 No aparecerá ningún contenido si el IDE de Visual Studio está en un idioma distinto del inglés, quita el contenido localizado y la casilla **Incluir contenido en inglés en todas las pestañas de navegación y las solicitudes de F1** del cuadro de diálogo **Opciones del Visor** está desactivada.  
  
#### Para quitar contenido  
  
1.  Elija la pestaña **Administrar contenido**.  
  
2.  En la lista de contenido, elija el vínculo **Quitar** junto al libro o libros que desea quitar.  
  
     El libro se agrega a la lista de **Cambios pendientes**.  
  
3.  Elija el botón de **Actualizar**.  
  
     El libro o libros que especificó se quitan de su equipo.  
  
## Actualizar el contenido local  
 La barra de estado indica cuándo hay disponibles actualizaciones para el contenido instalado.  
  
> [!IMPORTANT]
>  Si desea que el Visor de Ayuda busque automáticamente actualizaciones en línea, debe abrir el cuadro de diálogo **Opciones del Visor** y, a continuación, seleccione la casilla **Conectarse para comprobar actualizaciones de contenido**.  
  
#### Para actualizar el contenido local  
  
-   En la esquina inferior derecha de la barra de estado, elija el vínculo **Haga clic aquí para descargar ahora**.  
  
 Los tiempos de actualización pueden variar, pero puede ver el progreso de actualización en la barra de estado.  
  
## Mover el contenido local  
 Puede ahorrar espacio en disco moviendo contenido instalado en el equipo local a un recurso compartido de red o a otra partición en el equipo local.  
  
> [!IMPORTANT]
>  Para mover el contenido, debe iniciar sesión con una cuenta que tenga permisos administrativos.  
  
#### Para mover contenido local  
  
1.  En la pestaña **Administrar contenido**, elija el botón **Mover** en **Ruta de acceso del almacén local**.  
  
     Se abre el cuadro de diálogo **Mover contenido**.  
  
2.  En el cuadro de texto **Para**, escriba una ubicación diferente para el contenido y, a continuación, elija el botón **Aceptar**.  
  
3.  Elija el botón **Cerrar** cuando el contenido se termine de mover.  
  
## Vea también  
 [Visor de Ayuda de Microsoft](../ide/microsoft-help-viewer.md)