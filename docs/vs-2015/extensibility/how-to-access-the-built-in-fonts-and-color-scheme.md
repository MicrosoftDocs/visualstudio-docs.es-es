---
title: 'Cómo: obtener acceso a las fuentes integradas y a la combinación de colores | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a43fb3a22ecb2d04542eacf07bf883590868b75b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685309"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Cómo: Acceder al esquema integrado de fuentes y colores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El entorno de desarrollo integrado (IDE) de Visual Studio tiene un esquema de fuentes y colores que está asociado a la ventana del editor. Puede tener acceso a este esquema a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz.  
  
 Para usar la combinación de colores y fuentes integradas, un VSPackage debe:  
  
- Defina una categoría para usarla con el servicio fuentes y colores predeterminados.  
  
- Registre la categoría con el servidor de fuentes y colores predeterminados.  
  
- Aconseje al IDE que una ventana específica use los elementos y las categorías integrados para mostrar mediante las `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfaces y.  
  
  El IDE usa la categoría resultante como identificador de la ventana. El nombre de la categoría se muestra en el cuadro desplegable **Mostrar valores para:** de la página de propiedades **fuentes y colores** .  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Para definir una categoría usando fuentes y colores integrados  
  
1. Cree un GUID arbitrario.  
  
    Este GUID se usa para identificar de forma única una categoría<strong>.</strong> Esta categoría reutiliza la especificación predeterminada de fuentes y colores del IDE.  
  
   > [!NOTE]
   > Al recuperar datos de fuente y de color con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> u otras interfaces, los VSPackages usan este GUID para hacer referencia a información integrada.  
  
2. El nombre de la categoría se debe agregar a una tabla de cadenas dentro del archivo de recursos (. RC) del VSPackage, de modo que se pueda localizar según sea necesario cuando se muestre en el IDE.  
  
    Para obtener más información, vea [Agregar o eliminar una cadena](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Para registrar una categoría usando fuentes y colores integrados  
  
1. Construya un tipo especial de entrada de registro de categoría en la siguiente ubicación:  
  
     [Hklm\software\microsoft. \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<Category>* ]  
  
     *\<Category>* es el nombre no traducido de la categoría.  
  
2. Rellene el registro para usar las fuentes estándar y la combinación de colores con cuatro valores:  
  
    |Nombre|Tipo|data|Descripción|  
    |----------|----------|----------|-----------------|  
    |Category|REG_SZ|GUID|GUID arbitrario que identifica una categoría que contiene la fuente estándar y la combinación de colores.|  
    |Paquete|REG_SZ|GUID|F5E7E71D-1401-11D1-883B-0000F87579D2<br /><br /> Este GUID se usa en todos los VSPackages que usan las configuraciones predeterminadas de fuente y color.|  
    |NameID|REG_DWORD|Id.|El identificador de recurso de un nombre de categoría traducible en el VSPackage.|  
    |ToolWindowPackage|REG_SZ|GUID|GUID del VSPackage que implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz.|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Para iniciar el uso de fuentes y colores proporcionados por el sistema  
  
1. Cree una instancia de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interfaz como parte de la implementación e inicialización de la ventana.  
  
2. Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> método para obtener una instancia de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfaz correspondiente a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> instancia actual.  
  
3. Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> dos veces.  
  
   - Llame a una vez con `VSEDITPROPID_ViewGeneral_ColorCategory` como argumento.  
  
   - Llame a una vez con `VSEDITPROPID_ViewGeneral_FontCategory` como argumento.  
  
     Esto establece y expone los servicios de fuentes y colores predeterminados como una propiedad de la ventana.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se inicia el uso de fuentes y colores integrados.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte también  
 [Usar fuentes y colores](../extensibility/using-fonts-and-colors.md)   
 [Obtener información de fuente y color para la coloración del texto](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Obtener acceso a la configuración de fuente y color almacenada](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Información general sobre fuentes y colores](../extensibility/font-and-color-overview.md)
