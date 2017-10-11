---
title: Ensamblados privados | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 8ce054bf6149f0224785f4c3cd9274e86dc09d04
ms.openlocfilehash: e4c49a19a9befad5d90b9526842786f49af0851b
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="private-galleries"></a>Private Galleries
Puede compartir los controles, plantillas y herramientas que va a desarrollar enviándolas a una *Galería privada* en la intranet de su organización, como se indica a continuación:  
  
-   Crear un Atom (fuente RSS) a una ubicación central (repositorio) configurada de forma adecuada de la intranet. Para obtener más información, consulte [Cómo: crear una fuente Atom para una galería privada](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Distribuir un archivo .pkgdef que describe la Galería privada. Se recomienda esta configuración para los administradores que desean conectarse una galería privada en varios equipos al mismo tiempo.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Agregar una galería privada a extensiones y actualizaciones en Visual Studio  
 Cuando una galería privada está disponible, puede agregarlo a **extensiones y actualizaciones** en Visual Studio.  
  
 ![Administrador de extensiones de cuadro de diálogo Agregar](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Para agregar una galería privada a extensiones y actualizaciones  
  
1.  En la barra de menús, elija **Herramientas**, **Opciones**.  
  
2.  En el **entorno** nodo, seleccione **extensiones y actualizaciones**.  
  
3.  Elija el botón de **Agregar** .  
  
4.  En el **nombre** , a continuación, escriba un nombre para la Galería privada, por ejemplo, `My Gallery`.  
  
5.  En el **dirección URL** , escriba la dirección URL de la fuente Atom o un sitio de SharePoint que hospeda la Galería privada.  
  
    1.  Si el host es una fuente Atom que se conecta a la Galería privada, la dirección URL sería algo parecido a éste: http://www.mywebsite/mygallery/atom.xml.  Esta dirección URL puede hacer referencia a un archivo o una ruta de acceso de red.  
  
    2.  Si el host es un sitio de SharePoint, la dirección URL podría parecerse a este: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>Administrar ensamblados privados  
 Un administrador puede realizar una galería privada disponible en varios equipos al mismo tiempo modificando el registro del sistema en cada equipo. Para ello, cree un archivo .pkgdef que describe las nuevas claves del registro y sus valores.  El formato de este archivo es como sigue.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Para obtener más información, consulte [Cómo: administrar una privada Galería por uso de configuración del registro](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Instalar las extensiones de una galería privada  
 También puede buscar e instalar extensiones de Visual Studio desde una galería privada en **extensiones y actualizaciones**. Los pasos siguientes utilizan una galería privada denominada `My Gallery`.  
  
 ![Administrador de extensiones instalando una galería privada](../extensibility/media/em_.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Para buscar e instalar extensiones desde una galería privada  
  
1.  En la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
2.  En el panel izquierdo, seleccione **extensiones en línea**y, a continuación, seleccione **Galería mi**.  
  
3.  En el panel derecho, seleccione una extensión y, a continuación, elija la **descargar** botón.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Actualización de extensiones de una galería privada  
 Se publican nuevas versiones de extensiones de Visual Studio en la Galería privada, puede actualizar las extensiones que ha instalado. Los pasos siguientes utilizan una galería privada denominada `My Repository`.  
  
 ![Actualización de la Galería privada del Administrador de extensiones](../extensibility/media/em_update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Para actualizar una extensión instalada desde una galería privada  
  
1.  En la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
2.  En el panel izquierdo, seleccione **actualizaciones**y, a continuación, seleccione **repositorio Mis**.  
  
3.  En el panel derecho, seleccione una extensión y, a continuación, elija la **actualización** botón.  
  
## <a name="see-also"></a>Vea también  
 [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
