# [Documentação do depurador](index.md)
# Visão geral
## [Tour dos recursos do depurador](debugger-feature-tour.md)
# Guias de Início Rápido
## [Depurar um aplicativo gerenciado](quickstart-debug-with-managed.md)
## [Depurar um aplicativo nativo](quickstart-debug-with-cplusplus.md)
## [Depurar um aplicativo do ASP.NET](quickstart-debug-aspnet.md)
# Tutoriais
## [Aprenda a depurar usando o Visual Studio](getting-started-with-the-debugger.md)
## [Executando o código Python no depurador...](../python/vs-tutorial-01-04.md)
## [Depurar um aplicativo ativo do Azure](debug-live-azure-applications.md)
## [Exibir instantâneos usando o retrocesso do IntelliTrace](how-to-use-intellitrace-step-back.md)
# Guias de instruções
## [Navegar em código com o depurador](navigating-through-code-with-the-debugger.md)
## [Usar pontos de interrupção](using-breakpoints.md)
### [Solução de Problemas de ponto de interrupção](troubleshooting-breakpoints.md)
## [Inspecionar dados](debugger-windows.md)
### [Inspecionar variáveis](autos-and-locals-windows.md)
### [Definir uma inspeção em variáveis](watch-and-quickwatch-windows.md)
#### [Expressões no depurador](expressions-in-the-debugger.md)
##### [Especificadores de formato em C++](format-specifiers-in-cpp.md)
##### [Operador de contexto (C++)](context-operator-cpp.md)
##### [Especificadores de formato em C#](format-specifiers-in-csharp.md)
##### [Pseudovariáveis](pseudovariables.md)
### [Exibir valores de dados em Dicas de Dados](view-data-values-in-data-tips-in-the-code-editor.md)
### [Valores de cadeia de caracteres de exibição em um visualizador](string-visualizer-dialog-box.md)
### [Exibir o código de desmontagem](how-to-use-the-disassembly-window.md)
#### [Como rolar uma página para cima ou para baixo na memória](how-to-page-up-or-down-in-memory.md)
### [Exibir a pilha de chamadas](how-to-use-the-call-stack-window.md)
#### [Código misto e informações ausentes na janela Pilha de Chamadas](mixed-code-and-missing-information-in-the-call-stack-window.md)
#### [Como sair do código gerenciado quando quadros nativos estiverem ausentes da janela Pilha de Chamadas](how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md)
### [Exibir os valores do Registro](how-to-use-the-registers-window.md)
#### [Sobre a janela Registros](debugging-basics-registers-window.md)
#### [Como exibir e ocultar grupos de registros](how-to-display-and-hide-register-groups.md)
#### [Como editar um valor do Registro](how-to-edit-a-register-value.md)
### [Exibir memória para variáveis](memory-windows.md)
### [Inspecione as propriedades XAML durante a depuração](inspect-xaml-properties-while-debugging.md)
## [Exibir a pilha de chamadas](how-to-use-the-call-stack-window.md)
### [Criar um mapa visual da pilha de chamadas](map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
### [Código misto e informações ausentes na janela Pilha de Chamadas](mixed-code-and-missing-information-in-the-call-stack-window.md)
## [Edite o código e continuar a depuração](edit-and-continue.md)
### [Como habilitar e desabilitar Editar e Continuar](how-to-enable-and-disable-edit-and-continue.md)
### [Como parar as alterações de código](how-to-stop-code-changes.md)
### [Editar e continuar (Visual C++)](edit-and-continue-visual-cpp.md)
#### [Alterações de código com suporte (C++)](supported-code-changes-cpp.md)
### [Editar e continuar (Visual C#)](edit-and-continue-visual-csharp.md)
#### [Como usar Editar e Continuar (C#)](how-to-use-edit-and-continue-csharp.md)
#### [Alterações de código com suporte (C#)](supported-code-changes-csharp.md)
### [Editar e Continuar (Visual Basic)](edit-and-continue-visual-basic.md)
#### [Como aplicar edições no modo de interrupção com Editar e Continuar](how-to-apply-edits-in-break-mode-with-edit-and-continue.md)
#### [Edições sem suporte em Editar e Continuar do Visual Basic](unsupported-edits-in-visual-basic-edit-and-continue.md)
### [Não há suporte para Editar e Continuar em F#](edit-and-continue-not-supported-for-f-hash.md)
## Exibir dados do depurador
### [Exibir módulos](how-to-use-the-modules-window.md)
#### [Como localizar em qual DLL o programa falhou](how-to-find-which-dll-your-program-crashed-in.md)
### [Exibir documentos de script](how-to-view-script-documents.md)
## [Dicas e truques do depurador](debugger-tips-and-tricks.md)
### [Anexar aos processos em execução com o Depurador do Visual Studio](attach-to-running-processes-with-the-visual-studio-debugger.md)
### [Depurar em tempo de design](walkthrough-debugging-at-design-time.md)
### [Depurar usando o depurador Just-in-Time](debug-using-the-just-in-time-debugger.md)
#### [Como responder ao depurador Just-In-Time](just-in-time-debugging-in-visual-studio.md)
## Configurar a depuração
### [Gerenciar exceções com o depurador](managing-exceptions-with-the-debugger.md)
#### [Continuar a execução depois de uma exceção](continuing-execution-after-an-exception.md)
#### [Como examinar um código de sistema após uma exceção](how-to-examine-system-code-after-an-exception.md)
#### [Como usar verificações de tempo de execução nativas](how-to-use-native-run-time-checks.md)
##### [Personalização das verificações de tempo de execução nativas](native-run-time-checks-customization.md)
##### [Como escrever uma função de relatório de erro em tempo de execução](how-to-write-a-run-time-error-reporting-function.md)
##### [Usar verificações de tempo de execução sem a biblioteca em tempo de execução do C](using-run-time-checks-without-the-c-run-time-library.md)
### [Especificar arquivos de símbolo (.pdb) e de origem no depurador do Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
### [Depurar o código do usuário](just-my-code.md)
### [Preparação e configurações do depurador](debugger-settings-and-preparation.md)
#### [Configurações de projeto do depurador](debugger-project-settings.md)
##### [Como especificar configurações do depurador](how-to-specify-debugger-settings.md)
##### [Como definir configurações de depuração e versão](how-to-set-debug-and-release-configurations.md)
##### [Configurações do projeto para uma configuração de depuração de C++](project-settings-for-a-cpp-debug-configuration.md)
###### [Habilitar recursos de depuração no Visual C++ (-D_DEBUG)](enabling-debug-features-in-visual-cpp-d-debug.md)
##### [Configurações das páginas de propriedade para projetos Web](property-pages-settings-for-web-projects.md)
##### [Configurações do projeto para configurações de depuração de C#](project-settings-for-csharp-debug-configurations.md)
##### [Definições do projeto para uma configuração de depuração do Visual Basic](project-settings-for-a-visual-basic-debug-configuration.md)
#### [Depurar projetos DLL](debugging-dll-projects.md)
##### [Como depurar de um projeto de DLL](how-to-debug-from-a-dll-project.md)
##### [Como depurar no modo misto](how-to-debug-in-mixed-mode.md)
#### [Preparação de depuração: projetos de console](debugging-preparation-console-projects.md)
#### [Como depurar um executável que não faça parte de uma solução do Visual Studio](how-to-debug-an-executable-not-part-of-a-visual-studio-solution.md)
#### [Como depurar com a origem do Code Center Premium](how-to-debug-with-code-center-premium-source.md)
#### [Depuração e o processo de hospedagem](debugging-and-the-hosting-process.md)
#### [Como especificar uma versão do .NET Framework para depuração](how-to-specify-a-dotnet-framework-version-for-debugging.md)
### [Criar exibições personalizadas de dados](viewing-data-in-the-debugger.md)
#### [Criar exibições personalizadas de objetos nativos](create-custom-views-of-native-objects.md)
#### [Criar exibições personalizadas de objetos gerenciados](create-custom-views-of-dot-managed-objects.md)
##### [Usar o atributo DebuggerTypeProxy](using-debuggertypeproxy-attribute.md)
##### [Usar o atributo DebuggerDisplay](using-the-debuggerdisplay-attribute.md)
#### [Criar visualizadores personalizados de dados](create-custom-visualizers-of-data.md)
##### [Arquitetura do visualizador](visualizer-architecture.md)
##### [Passo a passo: escrever um visualizador em C#](walkthrough-writing-a-visualizer-in-csharp.md)
##### [Passo a passo: escrever um visualizador em Visual Basic](walkthrough-writing-a-visualizer-in-visual-basic.md)
##### [Como instalar um visualizador](how-to-install-a-visualizer.md)
##### [Como testar e depurar um visualizador](how-to-test-and-debug-a-visualizer.md)
##### [Considerações de segurança do visualizador](visualizer-security-considerations.md)
##### [Referência de API do visualizador](visualizer-api-reference.md)
### [Como restaurar comandos ocultos do depurador](how-to-restore-hidden-debugger-commands.md)
## [Depuração remota](remote-debugging.md)
### [Depuração remota do ASP.NET Core em um computador IIS](remote-debugging-aspnet-on-a-remote-iis-computer.md)
### [Depuração remota do ASP.NET em um computador IIS](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
### [Depuração remota ASP.NET no Azure](remote-debugging-azure.md)
### [Depuração remota de um projeto C# ou Visual Basic](remote-debugging-csharp.md)
### [Depuração remota de um projeto em C++](remote-debugging-cpp.md)
### [Atribuições de porta do depurador remoto](remote-debugger-port-assignments.md)
### [Configurar o Firewall do Windows para depuração remota](configure-the-windows-firewall-for-remote-debugging.md)
### [Erros e solução de problemas de depuração remota](remote-debugging-errors-and-troubleshooting.md)
#### [Erro: o Monitor de Depuração Remota do Microsoft Visual Studio no computador remoto não tem permissão para se conectar a este computador](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer.md)
#### [Ocorreu um erro de DCOM durante a tentativa de entrar em contato com o computador remoto. O acesso foi negado.](a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied.md)
#### [Erro: o Monitor de Depuração Remota do Microsoft Visual Studio no computador remoto está sendo executado como um usuário diferente](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md)
#### [Erro: não é possível intervir automaticamente no servidor](error-unable-to-automatically-step-into-the-server.md)
#### [Erro: falha no logon remoto do grupo de trabalho](error-workgroup-remote-logon-failure.md)
#### [Erro: falha na autenticação Kerberos](error-kerberos-authentication-failed.md)
#### [Erro: verifique se o DNS está configurado corretamente no computador de destino](error-ensure-that-dns-is-correctly-configured-on-the-target-computer.md)
#### [Erro: o Monitor de Depuração Remota do Microsoft Visual Studio (MSVSMON.EXE) parece não estar sendo executado no computador remoto.](error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running-on-the-remote-computer.md)
#### [Não foi possível se conectar ao Monitor de Depuração Remota do Microsoft Visual Studio](unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)
#### [Erro: não é possível iniciar a comunicação DCOM](error-unable-to-initiate-dcom-communication.md)
#### [Erro: o computador remoto não conseguiu iniciar as comunicações DCOM](error-remote-computer-could-not-initiate-dcom-communications.md)
#### [Erro: firewall no computador local](error-firewall-on-local-machine.md)
#### [Erro: firewall sem autenticação](error-firewall-no-authentication.md)
#### [Erro: o RPC requer autenticação](error-rpc-requires-authentication.md)
#### [Erro: você não tem permissão para inspecionar a identidade do processo](error-you-do-not-have-permission-to-inspect-the-process-s-identity.md)
#### [Erro: o serviço Depurador Remoto do Visual Studio no computador de destino não pode se reconectar a este computador](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)
#### [Erro: o processo de trabalho do site foi terminado pelo IIS](error-web-site-worker-process-has-been-terminated-by-iis.md)
#### [Erro: não é possível conectar ao computador <name>. O computador não pode ser encontrado na rede.](error-unable-to-connect-to-the-machine-name-the-machine-cannot-be-found-on-the-network.md)
#### [Erro: só há suporte para a depuração de modo misto quando se utiliza o Microsoft .NET Framework 2.0 ou superior](error-mixed-mode-debugging-is-supported-only-when-using-microsoft-dotnet-framework-2-0-or-greater.md)
#### [Erro: não há suporte para a depuração de modo misto para processos IA64](error-mixed-mode-debugging-for-ia64-processes-is-unsupported.md)
#### [Erro: só há suporte para a depuração de modo misto para processos x64 quando se utiliza o Microsoft .NET Framework 4 ou superior](error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-dotnet-framework-4-or-greater.md)
#### [Erro: O computador remoto não aparece em uma caixa de diálogo Conexões Remotas](error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)
## [Depurar aplicativos multi-threaded](debug-multithreaded-applications-in-visual-studio.md)
### [Começar a depurar aplicativos multithread](get-started-debugging-multithreaded-apps.md)
### [Ferramentas para depurar processos e threads](debug-threads-and-processes.md)
#### [Como usar a janela Pilhas Paralelas](using-the-parallel-stacks-window.md)
#### [Como usar a janela Inspeção Paralela](how-to-use-the-parallel-watch-window.md)
#### [Como usar a janela Threads](walkthrough-debugging-a-multithreaded-application.md)
#### [Como usar a janela Tarefas](using-the-tasks-window.md)
#### [Como usar a janela Threads da GPU](how-to-use-the-gpu-threads-window.md)
### [Depurar vários processos](debug-multiple-processes.md)
### [Passo a passo: depurar usando a janela Threads](how-to-use-the-threads-window.md)
### [Passo a passo: depurar um aplicativo paralelo](walkthrough-debugging-a-parallel-application.md)
### [Como mudar para outro thread durante a depuração](how-to-switch-to-another-thread-while-debugging.md)
### [Como sinalizar e remover sinalizador de threads](how-to-flag-and-unflag-threads.md)
### [Depurar em um cluster de alto desempenho](how-to-debug-on-a-high-performance-cluster.md)
### [Dicas para threads de depuração no código nativo](tips-for-debugging-threads-in-native-code.md)
### [Como definir um nome de thread em código nativo](how-to-set-a-thread-name-in-native-code.md)
### [Como definir um nome de thread em código gerenciado](how-to-set-a-thread-name-in-managed-code.md)
## [IntelliTrace](intellitrace.md)
### [Passo a passo: usando o IntelliTrace](walkthrough-using-intellitrace.md)
### [Recursos do IntelliTrace](intellitrace-features.md)
### [Depuração de histórico](historical-debugging.md)
### [Inspecionar seu aplicativo usando depuração histórica](historical-debugging-inspect-app.md)
### [Diagnosticar problemas após a implantação](diagnose-problems-after-deployment.md)
### [Usando o coletor IntelliTrace autônomo](using-the-intellitrace-stand-alone-collector.md)
### [Usando o Microsoft Monitoring Agent](using-the-microsoft-monitoring-agent.md)
### [Usando dados salvos do IntelliTrace](using-saved-intellitrace-data.md)
### [Referência de API para a extensibilidade do IntelliTrace](api-reference-for-intellitrace-extensibility.md)
## [Depurar os serviços do Azure](debug-azure-apps.md)
### [Depurar um aplicativo ativo do Azure](debug-live-azure-applications.md)
#### [Perguntas frequentes sobre depuração de instantâneos](debug-live-azure-apps-faq.md)
#### [Solução de problemas de depuração de instantâneos](debug-live-azure-apps-troubleshooting.md)
## [Depurar tipos específicos de aplicativo](debugging-applications.md)
### [Depurar aplicativos de 64 bits](debug-64-bit-applications.md)
### [Depurar aplicativos UWP](debugging-windows-store-and-windows-universal-apps.md)
#### [Iniciar uma sessão de depuração para um aplicativo UWP](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)
##### [Executar aplicativos UWP em um computador remoto](run-windows-store-apps-on-a-remote-machine.md)
##### [Executar aplicativos UWP no simulador](run-windows-store-apps-in-the-simulator.md)
##### [Implantar aplicativos UWP do Visual Studio](deploy-windows-store-apps-from-visual-studio.md)
#### [Depurar pacote de aplicativo instalado](debug-installed-app-package.md)
#### [Depurar XAML no Blend](debug-xaml-in-blend.md)
#### [Depurar HTML e CSS](quickstart-debug-html-and-css.md)
##### [Atualizar um aplicativo (JavaScript)](refresh-an-app-javascript.md)
##### [Depurar um controle WebView](debug-a-webview-control.md)
##### [Atalhos de teclado (HTML e JavaScript)](keyboard-shortcuts-html-and-javascript.md)
##### [Depurar códigos de exemplo HTML e CSS](debug-html-css-and-javascript-sample-code.md)
#### [Depurar o JavaScript usando o console](quickstart-debug-javascript-using-the-console.md)
##### [Comandos do Console JavaScript](javascript-console-commands.md)
#### [Como disparar eventos em segundo plano, de suspensão e de retomada](how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)
#### [Realizar pré-busca de conteúdo para aplicativos da Microsoft Store](prefetch-content-for-windows-store-apps.md)
### [Depurar código gerenciado](debugging-managed-code.md)
#### [Preparação de depuração: tipos de projeto C#, F# e Visual Basic](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
##### [Depuração gerenciada: configurações de propriedade recomendadas](managed-debugging-recommended-property-settings.md)
##### [Preparação da depuração: Aplicativos do Windows Forms](debugging-preparation-windows-forms-applications.md)
##### [Preparação de depuração: Serviços Windows](debugging-preparation-windows-services.md)
#### [Mensagens de diagnóstico na Janela de Saída](diagnostic-messages-in-the-output-window.md)
#### [Asserções em código gerenciado](assertions-in-managed-code.md)
#### [Instruções Stop no Visual Basic](stop-statements-in-visual-basic.md)
#### [Passo a passo: depurando um Windows Form](walkthrough-debugging-a-windows-form.md)
#### [Como depurar o método OnStart](how-to-debug-the-onstart-method.md)
#### [Depurar aplicativos de modo misto](debugging-mixed-mode-applications.md)
#### [Otimização e depuração JIT](jit-optimization-and-debugging.md)
#### [Depurar LINQ](debugging-linq.md)
#### [Erro: a depuração não é possível porque um depurador de kernel está habilitado no sistema](error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)
#### [Como depurar o código-fonte do .NET Framework](how-to-debug-dotnet-framework-source.md)
#### [Depurar WPF](debugging-wpf.md)
##### [Como usar o Visualizador de Árvore WPF](how-to-use-the-wpf-tree-visualizer.md)
##### [Como exibir informações de rastreamento de WPF](how-to-display-wpf-trace-information.md)
#### [Depurar F#](debugging-f-hash.md)
### [Depurar código nativo](debugging-native-code.md)
#### [Preparação de depuração: tipos de projeto do Visual C++](debugging-preparation-visual-cpp-project-types.md)
#### [Como depurar o código otimizado](how-to-debug-optimized-code.md)
#### [DebugBreak e __debugbreak](debugbreak-and-debugbreak.md)
#### [Asserções C/C++](c-cpp-assertions.md)
#### [Como depurar código assembly embutido](how-to-debug-inline-assembly-code.md)
#### [Técnicas de depuração MFC](mfc-debugging-techniques.md)
#### [Técnicas de depuração CRT](crt-debugging-techniques.md)
##### [Uso da biblioteca de depuração CRT](crt-debug-library-use.md)
##### [Macros para relatórios](macros-for-reporting.md)
##### [Versões de depuração das funções de alocação de heap](debug-versions-of-heap-allocation-functions.md)
##### [Detalhes do heap de depuração CRT](crt-debug-heap-details.md)
##### [Gravação da função de gancho de depuração](debug-hook-function-writing.md)
###### [Funções de gancho do bloco de clientes](client-block-hook-functions.md)
###### [Funções de gancho de alocação](allocation-hook-functions.md)
####### [Ganchos de alocação e alocações de memória de tempo de execução do C](allocation-hooks-and-c-run-time-memory-allocations.md)
###### [Funções de gancho de relatório](report-hook-functions.md)
##### [Como localizar perdas de memória usando a biblioteca CRT](finding-memory-leaks-using-the-crt-library.md)
#### [Perguntas frequentes de depuração de código nativo](debugging-native-code-faqs.md)
##### [Como posso depurar uma violação de acesso?](how-can-i-debug-an-access-violation-q.md)
##### [Como posso depurar violações de acesso ao executar meu programa fora do depurador?](how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger-q.md)
##### [Como posso saber se meus ponteiros corrompem um endereço de memória?](how-can-i-find-out-if-my-pointers-corrupt-a-memory-address-q.md)
##### [Como posso descobrir quem está passando um valor de parâmetro incorreto?](how-can-i-find-out-who-is-passing-a-wrong-parameter-value-q.md)
##### [Ao chamar uma função centenas de vezes, como sei qual chamada falhou?](when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed-q.md)
##### [Onde posso pesquisar códigos de erro Win32?](where-can-i-look-up-win32-error-codes-q.md)
##### [Como posso manter o foco ao passar pelo meu programa?](how-can-i-keep-focus-when-stepping-through-my-program-q.md)
##### [Como posso usar janelas do depurador durante a depuração de um programa em primeiro plano?](how-can-i-use-debugger-windows-while-debugging-a-foreground-program-q.md)
##### [Como posso depurar funções de API do Windows?](how-can-i-debug-windows-api-functions-q.md)
##### [Como retornar à função que chamou MFC em caso de interrupção](how-to-get-back-to-the-function-that-called-mfc-if-halted.md)
#### [Depuração de COM e ActiveX](com-and-activex-debugging.md)
##### [Depuração de servidor COM e contêiner](com-server-and-container-debugging.md)
###### [Como depurar servidores COM](how-to-debug-com-servers.md)
####### [Aplicativos de servidor SDI](sdi-server-applications.md)
###### [Como depurar clientes e servidores COM usando a depuração RPC](how-to-debug-com-clients-and-servers-using-rpc-debugging.md)
##### [Como depurar um controle ActiveX](how-to-debug-an-activex-control.md)
###### [Depurar um controle ActiveX com associação de dados](debugging-a-data-bound-activex-control.md)
##### [Ferramentas de depuração COM](com-debugging-tools.md)
#### [Como depurar código injetado](how-to-debug-injected-code.md)
### [Depurar o código GPU](debugging-gpu-code.md)
### [Diagnóstico de gráfico](graphics/TOC.md)
### [Depurar aplicativos ASP.NET](how-to-enable-debugging-for-aspnet-applications.md)
#### [Depuração do ASP.NET: requisitos do sistema](aspnet-debugging-system-requirements.md)
#### [Como executar o processo de trabalho em uma conta de usuário](how-to-run-the-worker-process-under-a-user-account.md)
#### [Como localizar o nome do processo ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
#### [Depurar aplicativos Web implantados](debugging-deployed-web-applications.md)
#### [Passo a passo: depurando um formulário Web](walkthrough-debugging-a-web-form.md)
#### [Como depurar exceções do ASP.NET](how-to-debug-aspnet-exceptions.md)
#### [Depurar aplicativos Web: erros e solução de problemas](debugging-web-applications-errors-and-troubleshooting.md)
##### [Depurar aplicativos Web: solução de problemas](debugging-web-applications-troubleshooting.md)
###### [Como verificar as configurações de propriedade do IIS](how-to-verify-iis-property-settings.md)
##### [Erro: o site usa endereço IP](error-site-uses-ip-address.md)
##### [Erro: falha em uma verificação de segurança porque o Serviço de Administração do IIS não respondeu](error-a-security-check-failed-because-the-iis-admin-service-did-not-respond.md)
##### [Erro: ASP.NET não instalado](error-aspnet-not-installed.md)
##### [Erro: falha na depuração porque a autenticação integrada do Windows não está habilitada](error-debugging-failed-because-integrated-windows-authentication-is-not-enabled.md)
##### [Erro: o servidor Web foi bloqueado e está bloqueando o verbo DEBUG](error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
##### [Erro: tempo limite durante a depuração de serviços Web](error-timeout-while-debugging-web-services.md)
##### [Erro: não foi possível iniciar a depuração no servidor Web](error-unable-to-start-debugging-on-the-web-server.md)
###### [Erro: o servidor Web não conseguiu localizar o recurso solicitado](error-the-web-server-could-not-find-the-requested-resource.md)
###### [Erro: o servidor Web não foi configurado corretamente](error-the-web-server-is-not-configured-correctly.md)
### [Depurar aplicativos Web](debugging-web-applications.md)
#### [Depuração de script do lado do cliente](client-side-script-debugging.md)
##### [Limitações na depuração de script](limitations-on-script-debugging.md)
##### [Como anexar ao script](how-to-attach-to-script.md)
###### [Aviso: depuração de script desabilitada](warning-script-debugging-disabled.md)
### [Depurar serviços WCF](debugging-wcf-services.md)
#### [Limitações da depuração de WCF](limitations-on-wcf-debugging.md)
#### [Como intervir em serviços WCF](how-to-step-into-wcf-services.md)
#### [Como depurar um serviço WCF auto-hospedado](how-to-debug-a-self-hosted-wcf-service.md)
## [Usar arquivos de despejo](using-dump-files.md)
### [API de extensibilidade de resumo do arquivo de despejo](dump-file-summary-extensibility-api.md)
## [Segurança do depurador](debugger-security.md)
# Referência
## [Referência da interface do usuário de depuração](debugging-user-interface-reference.md)
### [Caixa de diálogo Escolher Pontos de Interrupção](choose-breakpoints-dialog-box.md)
### [Caixa de diálogo Configurar Firewall para Depuração Remota](configure-firewall-for-remote-debugging-dialog-box.md)
### [Caixa de diálogo Depuração, Opções](debugging-options-dialog-box.md)
#### [Caixa de diálogo Geral, Depuração, Opções](general-debugging-options-dialog-box.md)
#### [Caixa de diálogo Just-In-Time, Depuração, Opções](just-in-time-debugging-options-dialog-box.md)
#### [Janela de Saída, Depuração, caixa de diálogo Opções](output-window-debugging-options-dialog-box.md)
### [Caixa de diálogo Visualizador de Conjunto de Dados](dataset-visualizer-dialog-box.md)
### [Caixa de diálogo Depurar Arquivos de Origem, Propriedades Comuns, Páginas de Propriedades da Solução](debug-source-files-common-properties-solution-property-pages-dialog-box.md)
### [Caixa de diálogo Editar e Continuar](edit-and-continue-dialog-box.md)
### [Caixa de diálogo Selecionar Tipo de Código](select-code-type-dialog-box.md)
### [Caixa de diálogo Parar Depuração em Andamento](stop-debugging-in-progress-dialog-box.md)
### [Caixa de diálogo Informações de Carregamento de Símbolos](symbol-load-information-dialog-box.md)
### [Caixa de diálogo Quando o Ponto de Interrupção é Atingido](when-breakpoint-is-hit-dialog-box.md)
### [Caixas de diálogo Depurando Erros e Aviso](debugging-errors-and-warning-dialog-boxes.md)
#### [Caixa de diálogo Falha na Asserção](assertion-failed-dialog-box.md)
#### [Caixa de diálogo Não É Possível Alterar o Valor](cannot-change-value-dialog-box.md)
#### [O depurador não pode exibir o código-fonte ou a desmontagem](debugger-cannot-display-source-code-or-disassembly.md)
#### [Caixa de diálogo Executável para Sessão de Depuração](executable-for-debugging-session-dialog-box.md)
#### [Caixa de diálogo Editar e Continuar (C++)](edit-and-continue-dialog-box-cpp.md)
#### [Caixa de diálogo do Depurador do Microsoft Visual Studio (Exceção Lançada)](microsoft-visual-studio-debugger-exception-thrown-dialog-box.md)
#### [Nenhuma origem disponível](no-source-available.md)
#### [Caixa de diálogo Resolver Ambiguidade](resolve-ambiguity-dialog-box.md)
#### [Caixa de diálogo Aviso de Código Obsoleto](stale-code-warning-dialog-box.md)
#### [Não é possível anexar ao processo](unable-to-attach-to-the-process.md)
#### [Caixa de diálogo de Mensagem de Erro de Editar e Continuar](edit-and-continue-error-message-dialog-box.md)
#### [Erro: a avaliação da função 'função' atingiu o tempo limite e precisou ser interrompida de forma não segura](error-evaluating-the-function-function-timed-out-and-needed-to-be-aborted-in-an-unsafe-way.md)
#### [Erro: não foi possível se conectar ao SQL Server no computador remoto](error-unable-to-connect-to-sql-server-on-remote-machine.md)
#### [Erro: não é possível acessar a interface de depuração do SQL Server](error-unable-to-access-the-sql-server-debugging-interface.md)
#### [Erro: o SQL não consegue localizar SSDEBUGPS](error-sql-can-t-find-ssdebugps.md)
#### [Erro: execução de Transact-SQL encerrada sem depuração](error-transact-sql-execution-ended-without-debugging.md)
#### [Erro: o usuário não conseguiu executar o procedimento armazenado sp_enable_sql_debug](error-user-could-not-execute-stored-procedure-sp-enable-sql-debug.md)
#### [Erro: o compartilhamento de arquivos do Windows foi configurado...](error-windows-file-sharing-has-been-configured-dot-dot-dot.md)
#### [Aviso de segurança: anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou você não tiver certeza, não anexe a esse processo](security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)
#### [Aviso de segurança: o depurador deve executar o comando não confiável](security-warning-debugger-must-execute-untrusted-command.md)
#### [Alerta de segurança do servidor de origem](source-server-security-alert.md)
#### [Só há suporte para a depuração de modo misto para processos x64 quando se utiliza o Microsoft .NET Framework 4 ou superior](mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoft-dotnet-framework-4-or-greater.md)
#### [Não há suporte para a depuração de modo misto para processos IA64.](mixed-mode-debugging-for-ia64-processes-is-unsupported.md)
#### [Só há suporte para a depuração de modo misto quando se utiliza o Microsoft .NET Framework 2.0 ou 3.0](mixed-mode-debugging-is-only-supported-when-using-microsoft-dotnet-framework-2-0-or-3-0.md)
## [SDK de Acesso à Interface de Depuração](debug-interface-access/debug-interface-access-sdk.md)
## [Ajuda do Spy++](spy-increment-help.md)
### [Usando Spy++](using-spy-increment.md)
#### [Introdução ao Spy++](introducing-spy-increment.md)
#### [Como iniciar o Spy++](how-to-start-spy-increment.md)
#### [Barra de ferramentas Spy++](spy-increment-toolbar.md)
#### [Como mostrar exibições do Spy++](how-to-display-spy-increment-views.md)
#### [Como atualizar a exibição](how-to-refresh-the-view.md)
#### [Como alterar fontes](how-to-change-fonts.md)
#### [Como expandir e recolher árvores do Spy++](how-to-expand-and-collapse-spy-increment-trees.md)
### [Exibições do Spy++](spy-increment-views.md)
#### [Exibição de janelas](windows-view.md)
##### [Como usar a ferramenta Localizador](how-to-use-the-finder-tool.md)
##### [Como pesquisar por uma janela na exibição de janelas](how-to-search-for-a-window-in-windows-view.md)
##### [Como exibir Propriedades da Janela](how-to-display-window-properties.md)
#### [Exibição de Mensagens](messages-view.md)
##### [Como controlar a exibição de mensagens](how-to-control-messages-view.md)
##### [Como abrir a exibição de mensagens da janela Localizar](how-to-open-messages-view-from-find-window.md)
##### [Como pesquisar por uma mensagem na exibição de Mensagens](how-to-search-for-a-message-in-messages-view.md)
##### [Como iniciar e parar a exibição de log de mensagem](how-to-start-and-stop-the-message-log-display.md)
##### [Códigos de mensagem](message-codes.md)
##### [Como exibir Propriedades da Mensagem](how-to-display-message-properties.md)
#### [Exibição de processos](processes-view.md)
##### [Como pesquisar por um processo na exibição de processos](how-to-search-for-a-process-in-processes-view.md)
##### [Como exibir as Propriedades do Processo](how-to-display-process-properties.md)
#### [Exibição de Threads](threads-view.md)
##### [Como pesquisar por um thread na exibição de threads](how-to-search-for-a-thread-in-threads-view.md)
##### [Como exibir Propriedades do Thread](how-to-display-thread-properties.md)
### [Referência a Spy++](spy-increment-reference.md)
#### [Comandos de menu](menu-commands.md)
##### [Comandos do menu do Spy](spy-menu-commands.md)
##### [Comandos do menu de árvore](tree-menu-commands.md)
##### [Comandos do menu Pesquisar](search-menu-commands.md)
##### [Comandos do menu Exibir](view-menu-commands.md)
##### [Comandos do menu Mensagens](messages-menu-commands.md)
##### [Comandos do menu Janela](window-menu-commands.md)
##### [Comandos do menu Ajuda](help-menu-commands.md)
#### [Caixa de diálogo Fonte (Ajuda do Microsoft Spy++)](font-dialog-box-microsoft-spy-increment-help.md)
#### [Ferramentas de pesquisa para as exibições do Spy++](search-tools-for-spy-increment-views.md)
##### [Caixa de diálogo Localizar Janela](find-window-dialog-box.md)
##### [Caixa de diálogo Pesquisa de Janela](window-search-dialog-box.md)
##### [Caixa de diálogo Pesquisa de Mensagens](message-search-dialog-box.md)
##### [Caixa de diálogo Pesquisa de Processos](process-search-dialog-box.md)
##### [Caixa de diálogo Pesquisa de Threads](thread-search-dialog-box.md)
#### [Caixa de diálogo Propriedades da Janela](window-properties-dialog-box.md)
##### [Guia Geral, Caixa de diálogo Propriedades da Janela](general-tab-window-properties-dialog-box.md)
##### [Guia Estilos, Caixa de diálogo Propriedades da Janela](styles-tab-window-properties-dialog-box.md)
##### [Guia Janelas, caixa de diálogo Propriedades da Janela](windows-tab-window-properties-dialog-box.md)
##### [Guia Classe, Caixa de diálogo Propriedades da Janela](class-tab-window-properties-dialog-box.md)
##### [Guia Processo, Caixa de diálogo Propriedades da Janela](process-tab-window-properties-dialog-box.md)
#### [Caixa de diálogo Opções de Mensagem](message-options-dialog-box.md)
##### [Guia Janelas, Caixa de diálogo Opções de Mensagem](windows-tab-message-options-dialog-box.md)
##### [Guia Mensagens, Caixa de diálogo Opções de Mensagem](messages-tab-message-options-dialog-box.md)
##### [Guia Saída, Caixa de diálogo Opções de Mensagem](output-tab-message-options-dialog-box.md)
#### [Caixa de diálogo Propriedades da Mensagem](message-properties-dialog-box.md)
#### [Caixa de diálogo Propriedades do Processo](process-properties-dialog-box.md)
##### [Guia Geral, Caixa de diálogo Propriedades do Processo](general-tab-process-properties-dialog-box.md)
##### [Guia Memória, Caixa de diálogo Propriedades do Processo](memory-tab-process-properties-dialog-box.md)
##### [Guia Arquivo de Paginação, Caixa de diálogo Propriedades do Processo](page-file-tab-process-properties-dialog-box.md)
##### [Guia Espaço, Caixa de diálogo Propriedades do Processo](space-tab-process-properties-dialog-box.md)
#### [Caixa de diálogo Propriedades do Thread](thread-properties-dialog-box.md)
##### [Guia Geral, Caixa de diálogo Propriedades do Thread](general-tab-thread-properties-dialog-box.md)
#### [Outras caixas de diálogo](other-dialog-boxes.md)
##### [Sobre o Microsoft Spy++](about-microsoft-spy-increment.md)
##### [Notificação de direitos autorais da Ajuda do Spy++](copyright-notice-for-spy-increment-help.md)
# Recursos
## [Novidades do depurador no Visual Studio](what-s-new-for-the-debugger-in-visual-studio.md)
