cmake_minimum_required(VERSION 3.20)
project(DualListDemo)

# MFC static link (1 = static, 2 = dynamic)
set(CMAKE_MFC_FLAG 1)

# Win32 application
set(CMAKE_WIN32_EXECUTABLE TRUE)

# Force static CRT (/MT for Release, /MTd for Debug)
set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

set(SOURCES
    StdAfx.cpp
    BankJiaoyi.cpp
    BeijingIntroDlg.cpp
    BitmapDialog.cpp
    BitmapPicture.cpp
    BossComeDlg.cpp
    BtnST.cpp
    BuyDlg.cpp
    Curvefit.cpp
    dib256.cpp
    dibpal.cpp
    Digistring.cpp
    DLGHTML.cpp
    DualListDemo.cpp
    DualListDemoDlg.cpp
    EnterBank.cpp
    Hispital.cpp
    HouseDlg.cpp
    HyperLink.cpp
    ListCtrlSortClass.cpp
    NetworkClub.cpp
    NewsDlg.cpp
    PostMoneyDlg.cpp
    ReplayLoad.cpp
    RichTop10.cpp
    RijiDlg.cpp
    SelectionDlg.cpp
    SellDlg.cpp
    SetUpGame.cpp
    ShengmingDlg.cpp
    StaticCounter.cpp
    StoryDlg.cpp
    Ticker.cpp
    TipDlg.cpp
    TopPlayerDlg.cpp
    Wangba.cpp
    DualListDemo.rc
)

add_executable(DualListDemo ${SOURCES})

# Preprocessor definitions
target_compile_definitions(DualListDemo PRIVATE
    WIN32
    _WINDOWS
    _MBCS
    _CRT_SECURE_NO_WARNINGS
    _CRT_NONSTDC_NO_WARNINGS
    _AFX_NO_MFC_CONTROLS_IN_DIALOGS
    $<$<CONFIG:Release>:NDEBUG>
    $<$<CONFIG:Debug>:_DEBUG>
)

# Compiler options: replace deprecated /GX with /EHsc, use /W2, permissive mode for old code
target_compile_options(DualListDemo PRIVATE
    /W2
    /EHsc
    /nologo
    /permissive
)

# Precompiled header: StdAfx.cpp creates it, all others use it
set_source_files_properties(StdAfx.cpp PROPERTIES
    COMPILE_FLAGS "/Yc\"stdafx.h\""
)

set(PCH_SOURCES
    BankJiaoyi.cpp
    BeijingIntroDlg.cpp
    BitmapDialog.cpp
    BitmapPicture.cpp
    BossComeDlg.cpp
    BtnST.cpp
    BuyDlg.cpp
    Curvefit.cpp
    dib256.cpp
    dibpal.cpp
    Digistring.cpp
    DLGHTML.cpp
    DualListDemo.cpp
    DualListDemoDlg.cpp
    EnterBank.cpp
    Hispital.cpp
    HouseDlg.cpp
    HyperLink.cpp
    ListCtrlSortClass.cpp
    NetworkClub.cpp
    NewsDlg.cpp
    PostMoneyDlg.cpp
    ReplayLoad.cpp
    RichTop10.cpp
    RijiDlg.cpp
    SelectionDlg.cpp
    SellDlg.cpp
    SetUpGame.cpp
    ShengmingDlg.cpp
    StaticCounter.cpp
    StoryDlg.cpp
    Ticker.cpp
    TipDlg.cpp
    TopPlayerDlg.cpp
    Wangba.cpp
)

set_source_files_properties(${PCH_SOURCES} PROPERTIES
    COMPILE_FLAGS "/Yu\"stdafx.h\" /FI\"stdafx.h\""
)

# Link libraries
target_link_libraries(DualListDemo PRIVATE winmm.lib)

# Windows subsystem is already set by CMAKE_WIN32_EXECUTABLE
