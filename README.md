
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>net6.0</TargetFramework>
        <Nullable>enable</Nullable>
        <!--Avalonia doesen't support TrimMode=link currently,but we are working on that https://github.com/AvaloniaUI/Avalonia/issues/6892 -->
        <TrimMode>copyused</TrimMode>
        <SelfContained>false</SelfContained>
        <BuiltInComInteropSupport>true</BuiltInComInteropSupport>
    </PropertyGroup>
    <ItemGroup>
        <!--This helps with theme dll-s trimming.
        If you will publish your application in self-contained mode with p:PublishTrimmed=true and it will use Fluent theme Default theme will be trimmed from the output and vice versa.
        https://github.com/AvaloniaUI/Avalonia/issues/5593 -->
        <TrimmableAssembly Include="Avalonia.Themes.Fluent" />
        <TrimmableAssembly Include="Avalonia.Themes.Default" />
    </ItemGroup>
    <ItemGroup>
        <PackageReference Include="Avalonia.Desktop" Version="11.0.0-preview4" />
        <!--Condition below is needed to remove Avalonia.Diagnostics package from build output in Release configuration.-->
        <PackageReference Condition="'$(Configuration)' == 'Debug'" Include="Avalonia.Diagnostics" Version="11.0.0-preview4" />
        <PackageReference Condition="'$(Configuration)' != 'Debug'" Include="Costura.Fody" Version="5.7.0">
          <PrivateAssets>all</PrivateAssets>
          <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
        </PackageReference>
    </ItemGroup>
    <ItemGroup>
        <ProjectReference Include="..\DirectPackageInstaller\DirectPackageInstaller.csproj" />
    </ItemGroup>
</Project>
