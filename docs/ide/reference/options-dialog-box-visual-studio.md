---
title: "Opciones (Cuadro de di&#225;logo) (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.toolsoptionspages"
helpviewer_keywords: 
  - "configuración de opciones de herramientas"
  - "Opciones (cuadro de diálogo)"
  - "Cuadro de diálogo Opciones, entorno de desarrollo"
  - "herramientas [Visual Studio], personalizar"
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opciones (Cuadro de di&#225;logo) (Visual Studio)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El cuadro de diálogo **Opciones** le permite configurar el entorno de desarrollo integrado \(IDE\) de acuerdo con sus necesidades.  Por ejemplo, puede establecer una ubicación predeterminada para guardar los proyectos, cambiar la apariencia y el comportamiento predeterminados de las ventanas, y crear accesos directos para los comandos que más utiliza.  También hay opciones específicas de su lenguaje de desarrollo y su plataforma.  Puede tener acceso a **Opciones** desde el menú **Herramientas**.  
  
> [!NOTE]
>  Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Diseño del cuadro de diálogo Opciones  
 El cuadro de diálogo **Opciones** está dividido en dos partes: un panel de navegación a la izquierda y un área de presentación a la derecha.  El control de árbol del panel de navegación incluye nodos de carpeta, como Entorno, Editor de texto, Proyectos y soluciones, y Control de código fuente.  Expanda cualquier nodo de carpeta para ver las páginas de opciones que contiene.  Cuando selecciona el nodo de una página determinada, sus opciones aparecen en el área de presentación.  
  
 Las opciones para una característica del IDE no aparecen en el panel de navegación hasta que la característica no está cargada en memoria.  Por tanto, puede que no se muestren las mismas opciones cuando inicia una nueva sesión que cuando finalizó la última sesión.  Cuando crea un proyecto o ejecuta un comando que utiliza una aplicación determinada, se agregan nodos para las opciones correspondientes al cuadro de diálogo Opciones.  Estas opciones agregadas permanecerán disponibles mientras la característica del IDE esté en memoria.  
  
> [!NOTE]
>  Algunas colecciones de configuraciones tienen como ámbito el número de páginas que aparecen en el panel de navegación del cuadro de diálogo Opciones.  Puede ver todas las páginas posibles si selecciona **Mostrar todas las configuraciones**.  
  
## Cómo se aplican las opciones  
 Al hacer clic en Aceptar en el cuadro de diálogo **Opciones** se guardan todas las configuraciones de todas las páginas.  Al hacer clic en Cancelar en cualquier página se cancelan todas las solicitudes de cambios, incluidas las realizadas en otras páginas del cuadro de diálogo **Opciones**.  Algunos cambios en la configuración de opciones, como los realizados en [Fuentes y colores, Entorno, Opciones \(Cuadro de diálogo\)](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), sólo surtirán efecto después de cerrar y volver a abrir Visual Studio.  
  
### Mostrar todas las configuraciones  
 La selección o la anulación de la selección de **Mostrar todas las configuraciones** aplica todos los cambios realizados en el cuadro de diálogo **Opciones**, aunque no se haya hecho clic en **Aceptar**.  
  
## Vea también  
 [Personalizar el editor](../../ide/customizing-the-editor.md)