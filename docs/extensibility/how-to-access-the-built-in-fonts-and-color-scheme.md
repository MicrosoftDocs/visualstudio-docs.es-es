---
title: Procedimiento Obtener acceso a la combinación de colores y fuentes integradas | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58d5fd0bfe1c8d5f5896d365a7b0ecfdb8da25b3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068228"
---
# <a name="how-to-access-the-built-in-fonts-and-color-ccheme"></a>Procedimiento Obtener acceso a las fuentes integradas y ccheme de color
El entorno de desarrollo integrado (IDE) de Visual Studio tiene un esquema de fuentes y colores que está asociado a la ventana del editor. Puede tener acceso a este esquema a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz.

 Para usar las fuentes integradas y la combinación de colores, un VSPackage debe:

- Definir una categoría para usar con el servicio de forma predeterminada, las fuentes y colores.

- Registre la categoría con el servidor de forma predeterminada, las fuentes y colores.

- Indicar que al IDE que una ventana específica usa las categorías y los elementos de visualización integradas mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> interfaces.

  El IDE usa la categoría resultante como un identificador de la ventana. Nombre de la categoría se muestra en el **mostrar valores para:** cuadro desplegable en la **fuentes y colores** página de propiedades.

## <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Para definir una categoría de uso de colores y fuentes integradas

1. Cree un GUID arbitrario.

     Este GUID se utiliza para identificar de forma exclusiva una categoría. Se vuelve a utilizar en esta categoría especificación de colores y fuentes de forma predeterminada del IDE.

    > [!NOTE]
    >  Cuando se recuperan datos de fuente y color con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> o de otras interfaces, los paquetes VSPackage usar este GUID para hacer referencia a información integrada.

2. Nombre de la categoría debe agregarse a una tabla de cadenas dentro de los recursos de VSPackage (*.rc*) de archivos, por lo que se puede localizar según sea necesario cuando se muestra en el IDE.

     Para obtener más información, consulte [agregar o eliminar una cadena](/cpp/windows/adding-or-deleting-a-string).

### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Para registrar una categoría de uso de colores y fuentes integradas

1. Construir un tipo especial de entrada de registro de la categoría en la siguiente ubicación:

     *[HKLM\SOFTWARE\Microsoft \Visual Studio\\\<Visual Studio version>\FontAndColors\\\<Category>*]

     *\<Categoría >* es el nombre no traducido de la categoría.

2. Rellenar el registro para usar la combinación de colores y fuentes estándar con cuatro valores:

    |Name|Tipo|Datos|Descripción|
    |----------|----------|----------|-----------------|
    |Categoría|REG_SZ|GUID|Un GUID arbitrario que identifica una categoría que contiene el esquema de color y fuente de cotizaciones.|
    |Paquete|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Este GUID se usa por todos los VSPackages que usan las configuraciones predeterminadas de fuente y color.|
    |NameID|REG_DWORD|ID|El identificador de recurso de un nombre de categoría traducible en el VSPackage.|
    |ToolWindowPackage|REG_SZ|GUID|El GUID del VSPackage que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz.|

### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Para iniciar el uso de colores y fuentes proporcionados por el sistema

1. Cree una instancia de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaz como parte de la implementación y la inicialización de la ventana.

2. Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> método para obtener una instancia de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> interfaz correspondiente a la actual <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> instancia.

3. Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> dos veces.

   - Llame a la vez con `VSEDITPROPID_ViewGeneral_ColorCategory`como argumento.

   - Llame a la vez con `VSEDITPROPID_ViewGeneral_FontCategory` como argumento.

     Esto establece y expone los servicios de fuentes y colores predeterminados como una propiedad de la ventana.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente inicia el uso de colores y fuentes integradas.

```cpp
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

## <a name="see-also"></a>Vea también

- [Utilizar fuentes y colores](../extensibility/using-fonts-and-colors.md)
- [Obtener información de fuente y color de coloración de texto](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Acceso a la configuración de fuente y color almacenada](../extensibility/accessing-stored-font-and-color-settings.md)
- [Información general de fuente y color](../extensibility/font-and-color-overview.md)