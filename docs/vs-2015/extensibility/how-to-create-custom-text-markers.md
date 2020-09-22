---
title: 'Cómo: crear marcadores de texto personalizados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842382"
---
# <a name="how-to-create-custom-text-markers"></a>Cómo: Crear marcadores de texto personalizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si desea crear un marcador de texto personalizado para resaltar u organizar el código, debe realizar los siguientes pasos:  
  
- Registra el nuevo marcador de texto para que otras herramientas puedan tener acceso a él.  
  
- Proporcionar una implementación y configuración predeterminadas del marcador de texto  
  
- Cree un servicio que puedan usar otros procesos para hacer uso del marcador de texto.  
  
  Para obtener más información sobre cómo aplicar un marcador de texto a una región de código, vea [Cómo: usar marcadores de texto](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Para registrar un marcador personalizado  
  
1. Cree una entrada del registro de la siguiente manera:  
  
    HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \Text Editor\External\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID></em>es un `GUID` que se usa para identificar el marcador que se va a agregar.  
  
    *\<Version>* es la versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , por ejemplo 8,0  
  
    *\<PackageGUID>* es el GUID del VSPackage que implementa el objeto de automatización.  
  
   > [!NOTE]
   > La ruta de acceso raíz de HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* se puede invalidar con una raíz alternativa cuando se inicializa el shell de Visual Studio. para obtener más información, vea [Modificadores](../extensibility/command-line-switches-visual-studio-sdk.md)de la línea de comandos.  
  
2. Cree cuatro valores en HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \Text Editor\External marcadores\\*\<MarkerGUID>*  
  
   - (Es el valor predeterminado).  
  
   - Servicio  
  
   - DisplayName  
  
   - Paquete  
  
   - `Default` es una entrada opcional de tipo REG_SZ. Cuando se establece, el valor de la entrada es una cadena que contiene información de identificación útil, por ejemplo "marcador de texto personalizado".  
  
   - `Service` es una entrada de tipo REG_SZ que contiene la cadena GUID del servicio que proporciona el marcador de texto personalizado por proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> . El formato es {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
   - `DisplayName` es una entrada de tipo REG_SZ que contiene el identificador de recurso del nombre del marcador de texto personalizado. El formato es #YYYY.  
  
   - `Package` es una entrada de tipo REG_SZ que contiene el `GUID` de VSPackage que proporciona el servicio que se muestra en servicio. El formato es {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Para crear un marcador de texto personalizado  
  
1. Implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     La implementación de esta interfaz define el comportamiento y la apariencia del tipo de marcador personalizado.  
  
     Se llama a esta interfaz cuando  
  
    1. Un usuario inicia el IDE por primera vez.  
  
    2. Un usuario selecciona el botón **Restablecer valores predeterminados** en la página de propiedades **fuentes y colores** de la carpeta **entorno** , que se encuentra en el panel izquierdo del cuadro de diálogo **Opciones** obtenido en el menú **herramientas** del IDE.  
  
2. Implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> método, especificando qué `IVsPackageDefinedTextMarkerType` implementación se debe devolver según el GUID de tipo de marcador especificado en la llamada al método.  
  
     El entorno llama a este método la primera vez que se crea el tipo de marcador personalizado y especifica un GUID que identifica el tipo de marcador personalizado.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Para ofrecer el tipo de marcador como servicio  
  
1. Llame al <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> método para <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> .  
  
     Se devuelve un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> .  
  
2. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> método, especificando el GUID que identifica el servicio de tipo de marcador personalizado y proporcionando un puntero a la implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaz. La <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementación debe devolver un puntero a la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interfaz.  
  
     Una cookie única que identifica que se devuelve el servicio. Posteriormente, puede usar esta cookie para revocar el servicio de tipo de marcador personalizado mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> método de la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaz que especifica este valor de cookie.  
  
## <a name="see-also"></a>Consulte también  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)   
 [Cómo: implementar marcadores de error](../extensibility/how-to-implement-error-markers.md)   
 [Cómo: Usar marcadores de texto](../extensibility/how-to-use-text-markers.md)
