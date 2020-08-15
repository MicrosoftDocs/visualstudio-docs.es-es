---
title: Registrando un lenguaje heredado Service1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0076eeee0ebcb0a80925efdde212097a3ec3e7e
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238886"
---
# <a name="registering-a-legacy-language-service-1"></a>Registro de un servicio de lenguaje heredado 1
En Managed Package Framework (MPF), el servicio de lenguaje es ofrecidos por un VSPackage (vea [VSPackages](../../extensibility/internals/vspackages.md)) y se registra con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] agregando claves y entradas del registro. Este proceso de registro se realiza en parte durante la instalación y en parte en tiempo de ejecución.

## <a name="register-the-language-service-by-using-attributes"></a>Registrar el servicio de lenguaje mediante atributos
 Los atributos siguientes se usan para registrar un servicio de lenguaje.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Estos atributos se explican a continuación.

### <a name="provideserviceattribute"></a>ProvideServiceAttribute
 Este atributo registra el servicio de lenguaje como servicio.

### <a name="example"></a>Ejemplo

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideServiceAttribute(typeof(TestLanguageService),
                             ServiceName = "Test Language Service")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute
 Este atributo registra el servicio de lenguaje específicamente como un servicio de lenguaje. Permite establecer las opciones que especifican las características que ofrece el servicio de lenguaje. En el ejemplo se muestra un subconjunto de las opciones que un servicio de lenguaje puede proporcionar. Para obtener el conjunto completo de opciones del servicio de lenguaje, vea <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> .

### <a name="example"></a>Ejemplo

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),
                             "Test Language",
                             106,             // resource ID of localized language name
                             CodeSense = true,             // Supports IntelliSense
                             RequestStockColors = false,   // Supplies custom colors
                             EnableCommenting = true,      // Supports commenting out code
                             EnableAsyncCompletion = true  // Supports background parsing
                             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute
 Este atributo asocia su servicio de lenguaje a una extensión de archivo. Cada vez que se carga un archivo con esa extensión, en cualquier proyecto se inicia el servicio de lenguaje y se usa para mostrar el contenido del archivo.

### <a name="example"></a>Ejemplo

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),
                                       ".Testext")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguagecodeexpansionattribute"></a>ProvideLanguageCodeExpansionAttribute
 Este atributo registra una ubicación de la que se obtienen la expansión de código o las plantillas de fragmento de código. El **Explorador de fragmentos de código** y el editor usan esta información cuando se inserta un fragmento de código en el archivo de código fuente.

### <a name="example"></a>Ejemplo

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageCodeExpansionAttribute(
             typeof(TestLanguageService),
             "Test Language", // Name of language used as registry key.
             106,           // Resource ID of localized name of language service.
             "testlanguage",  // language key used in snippet templates.
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageeditoroptionpageattribute"></a>ProvideLanguageEditorOptionPageAttribute
 Este atributo registra una página de propiedades que se mostrará en el cuadro de diálogo **Opciones** en la categoría **Editor de texto** . Use uno de estos atributos para cada página que se va a mostrar para el servicio de lenguaje. Si necesita organizar las páginas en una estructura de árbol, use atributos adicionales para definir cada nodo del árbol.

### <a name="example"></a>Ejemplo
 En este ejemplo se muestran dos páginas de propiedades, **Opciones** y **sangría**, y un nodo que contiene la segunda página de propiedades.

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Options",      // Registry key name for property page
             "#242",         // Localized name of property page
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Advanced",     // Registry key name for node
             "#243",         // Localized name of node
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             @"Advanced\Indenting",     // Registry key name for property page
             "#244",         // Localized name of property page
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

## <a name="proffer-the-language-service-at-run-time"></a>Ofrecer el servicio de lenguaje en tiempo de ejecución
 Cuando se cargue el paquete de idioma, debe indicar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que el servicio de lenguaje está listo. Para ello, proffering el servicio. Esto se hace en el método <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>. Además, debe iniciar un temporizador que llame al servicio de lenguaje durante períodos de inactividad, de modo que se pueda realizar el análisis en segundo plano. Este temporizador inactivo también se utiliza para actualizar las propiedades del documento si ha implementado a través de la <xref:Microsoft.VisualStudio.Package.DocumentProperties> clase. Para admitir un temporizador, el paquete debe implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> interfaz (solo <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> es necesario implementar completamente el método; los métodos restantes pueden devolver valores predeterminados).

### <a name="example"></a>Ejemplo
 Este ejemplo muestra un enfoque típico para profferingr un servicio y proporcionar un temporizador inactivo.

```csharp

using System;
using System.Runtime.InteropServices;
using System.ComponentModel.Design;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.OLE.Interop;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,
        AutoOutlining = true,
        EnableCommenting = true,
        MatchBraces = true,
        ShowMatchingBrace = true)]
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package

    public class TestLanguagePackage : Package, IOleComponent
    {
        private uint m_componentID;

        protected override void Initialize()
        {
            base.Initialize();  // required

            // Proffer the service.
            IServiceContainer serviceContainer = this as IServiceContainer;
            TestLanguageService langService      = new TestLanguageService();
            langService.SetSite(this);
            serviceContainer.AddService(typeof(TestLanguageService),
                                        langService,
                                        true);

            // Register a timer to call our language service during
            // idle periods.
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                       as IOleComponentManager;
            if (m_componentID == 0 && mgr != null)
            {
                OLECRINFO[] crinfo = new OLECRINFO[1];
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal |
                                              (uint)_OLECADVF.olecadvfRedrawOff |
                                              (uint)_OLECADVF.olecadvfWarningsOff;
                crinfo[0].uIdleTimeInterval = 1000;
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);
            }
        }

        protected override void Dispose(bool disposing)
        {
            if (m_componentID != 0)
            {
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                           as IOleComponentManager;
                if (mgr != null)
                {
                    int hr = mgr.FRevokeComponent(m_componentID);
                }
                m_componentID = 0;
            }

            base.Dispose(disposing);
        }

        #region IOleComponent Members

        public int FDoIdle(uint grfidlef)
        {
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;
            // Use typeof(TestLanguageService) because we need to
            // reference the GUID for our language service.
            LanguageService service = GetService(typeof(TestLanguageService))
                                      as LanguageService;
            if (service != null)
            {
                service.OnIdle(bPeriodic);
            }
            return 0;
        }

        public int FContinueMessageLoop(uint uReason,
                                        IntPtr pvLoopData,
                                        MSG[] pMsgPeeked)
        {
            return 1;
        }

        public int FPreTranslateMessage(MSG[] pMsg)
        {
            return 0;
        }

        public int FQueryTerminate(int fPromptUser)
        {
            return 1;
        }

        public int FReserved1(uint dwReserved,
                              uint message,
                              IntPtr wParam,
                              IntPtr lParam)
        {
            return 1;
        }

        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)
        {
            return IntPtr.Zero;
        }

        public void OnActivationChange(IOleComponent pic,
                                       int fSameComponent,
                                       OLECRINFO[] pcrinfo,
                                       int fHostIsActivating,
                                       OLECHOSTINFO[] pchostinfo,
                                       uint dwReserved)
        {
        }

        public void OnAppActivate(int fActive, uint dwOtherThreadID)
        {
        }

        public void OnEnterState(uint uStateID, int fEnter)
        {
        }

        public void OnLoseActivation()
        {
        }

        public void Terminate()
        {
        }

        #endregion
    }
}
```
