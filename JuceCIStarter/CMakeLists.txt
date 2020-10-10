# Declare plugin target with configuration
juce_add_plugin(JuceCIStarter
    VERSION 0.0.1
    PLUGIN_MANUFACTURER_CODE Code
    PLUGIN_CODE Cod3
    FORMATS AU VST3
    PRODUCT_NAME "JUCE CI Starter")

# Generate the JUCE header file for our source code
juce_generate_juce_header(JuceCIStarter)

# Add source files to target
target_sources(JuceCIStarter PRIVATE
    Source/PluginEditor.cpp
    Source/PluginProcessor.cpp)

# Provide preprocessor definitions for JUCE
target_compile_definitions(JuceCIStarter PUBLIC
    JUCE_WEB_BROWSER=0
    JUCE_USE_CURL=0
    JUCE_VST3_CAN_REPLACE_VST2=0)

# Link JUCE audio utils library to plugin target
target_link_libraries(JuceCIStarter PRIVATE
    juce::juce_audio_utils)