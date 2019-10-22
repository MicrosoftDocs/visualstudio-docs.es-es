---
title: Procedimiento Crear marcadores de texto personalizado | Documentos de Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435981"
---
# <a name="how-to-create-custom-text-markers"></a>Procedimiento Crear marcadores de texto personalizado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si desea crear un marcador de texto personalizado para enfatizar u organizar el código, debe realizar los pasos siguientes:  
  
- Registre el nuevo marcador de texto, para que otras herramientas de acceso a él  
  
- Proporcionar una implementación predeterminada y la configuración del marcador de texto  
  
- Crear un servicio que puede usarse por otros procesos para hacer uso de marcador de texto  
  
  Para obtener más información sobre cómo aplicar un marcador de texto a una región de código, vea [Cómo: Utilizar marcadores de texto](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Para registrar un identificador personalizado  
  
1. Cree una entrada del registro de la manera siguiente:  
  
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<Version>* \Text Editor\External Markers\\ *\<MarkerGUID>*  
  
    <em>\<MarkerGUID ></em>es un `GUID` usado para identificar el marcador que se va a agregar  
  
    *\<Versión >* es la versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], por ejemplo 8.0  
  
    *\<PackageGUID >* es el GUID del VSPackage implementa el objeto de automatización.  
  
   > [!NOTE]
   > La ruta de acceso raíz de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<versión >* puede reemplazarse por una raíz alternativa cuando se inicializa el shell de Visual Studio, para obtener más información, vea [Modificadores de línea de comandos](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Cree cuatro valores en HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<versión >* \Text Editor\External marcadores\\ *\<MarkerGUID >*  
  
   - (Predeterminado)  
  
   - web de Office  
  
   - DisplayName  
  
   - Paquete  
  
   - `Default` es una entrada opcional del tipo REG_SZ. Cuando se establece, el valor de la entrada es una cadena que contiene la identificación información útil, por ejemplo "marcador de texto personalizado".  
  
   - `Service` es una entrada del tipo REG_SZ que contiene la cadena de GUID del servicio que proporciona el marcador de texto personalizado mediante proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. El formato es {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
   - `DisplayName` es una entrada del tipo REG_SZ que contiene el identificador de recurso del nombre del marcador de texto personalizado. El formato es #YYYY.  
  
   - `Package` entrada de tipo REG_SZ que contenga el `GUID` de VSPackage que proporciona el servicio aparece en el servicio. El formato es {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Para crear un marcador de texto personalizado  
  
1. Implementar la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     La implementación de esta interfaz define el comportamiento y apariencia de su tipo de marcador personalizado.  
  
     Se llama a esta interfaz cuando  
  
    1. Un usuario inicia el IDE por primera vez.  
  
    2. Un usuario selecciona el **Restablecer valores predeterminados** situado bajo el **fuentes y colores** página de propiedades de la **entorno** carpeta, que se encuentra en el panel izquierdo de la  **Opciones de** obtenido del cuadro de diálogo de la **herramientas** menú del IDE.  
  
2. Implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> método, especificando que `IVsPackageDefinedTextMarkerType` implementación se debe devolver en función del tipo de marcador GUID especificado en la llamada al método.  
  
     El entorno llama a este momento el primer método se crea el tipo de marcador personalizado y especifica un GUID que identifica el tipo de marcador personalizado.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Para ofrecer el tipo de marcador como un servicio  
  
1. Llame a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> método para <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> se devuelve.  
  
2. Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> método, especificando el GUID que identifica el servicio de tipo de marcador personalizado y proporcionar un puntero a la implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfaz. Su <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementación debe devolver un puntero a la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interfaz.  
  
     Una cookie única que identifica se devuelve el servicio. Posteriormente, puede usar esta cookie para revocar su servicio de tipo de marcador personalizado mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> método de la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaz si se especifica este valor de cookie.  
  
## <a name="see-also"></a>Vea también  
 [Uso de marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Cómo: Agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)   
 [Cómo: Implementar los marcadores de Error](../extensibility/how-to-implement-error-markers.md)   
 [Cómo: Usar marcadores de texto](../extensibility/how-to-use-text-markers.md)
