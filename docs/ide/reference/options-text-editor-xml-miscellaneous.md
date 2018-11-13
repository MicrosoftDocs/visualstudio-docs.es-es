---
title: Opciones, editor de texto, XML y varios
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c6def0a2e374e5297d25d17f4ea4a4a113d4bd56
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673283"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opciones, editor de texto, XML y varios
Use la página de propiedades **Varios** para cambiar las opciones de finalización automática y esquema del Editor XML. Para abrir el cuadro de diálogo **Opciones**, haga clic en el menú **Herramientas** y, después, en **Opciones**. Para acceder a la página de propiedades **Varios**, expanda el nodo **Editor de texto** > **XML** > **Varios**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="auto-insert"></a>Inserción automática  
**Etiquetas de cierre**  
El editor de texto agrega etiquetas de cierre al crear elementos XML. Si se selecciona una etiqueta de inicio de elemento, el editor inserta la etiqueta de cierre correspondiente, incluido un prefijo de espacio de nombres coincidente. Esta casilla se encuentra activada de forma predeterminada.  
  
**Comillas de atributo**  
Al crear atributos XML, el editor inserta los caracteres `="` y `"` y coloca el carácter de intercalación (**^**) dentro de las comillas. Esta casilla se encuentra activada de forma predeterminada.  
  
**Declaraciones de espacio de nombres**  
El editor inserta automáticamente declaraciones de espacio de nombres siempre que se necesitan. Esta casilla se encuentra activada de forma predeterminada.  
  
**Otro marcado (comentarios, CDATA)**  
Se completan automáticamente comentarios, CDATA, DOCTYPE, instrucciones de procesamiento y otro marcado. Esta casilla se encuentra activada de forma predeterminada.  
  
## <a name="network"></a>Red  
**Descargar automáticamente DTD y esquemas**  
Los esquemas y las definiciones de tipo de documento (DTD) se descargan automáticamente desde ubicaciones HTTP. Esta característica usa System.Net con la detección automática del servidor proxy habilitada. Esta casilla se encuentra activada de forma predeterminada.  
  
## <a name="outlining"></a>esquematizar  
**Especificar el modo de esquematización al abrir los archivos**  
Activa la característica de esquematización cuando se abre un archivo. Esta casilla se encuentra activada de forma predeterminada.  
  
## <a name="caching"></a>Almacenamiento en memoria caché  
**Esquemas**  
Especifica la ubicación de la caché de esquema. El botón Examinar (...) abre la ubicación actual de la caché de esquema en una nueva ventana. La ubicación predeterminada es *\<Directorio de instalación de Management Studio>* \Xml\Schemas.  
  
## <a name="see-also"></a>Vea también
- [Cómo: Crear documentación XML en Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Generación de código](../code-generation-in-visual-studio.md)
