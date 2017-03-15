platform :ios, '8.0'

inhibit_all_warnings!

target 'ReactNativeMissingFile' do
    # React
    pod 'React', :path => './Other Sources/ReactNative', :subspecs => [
      'Core',
      'RCTImage',
      'RCTNetwork',
      'RCTText',
      'RCTWebSocket',
      # Add any other subspecs you want to use in your project
      'ART',
      'RCTActionSheet',
      'RCTAdSupport',
      'RCTCameraRoll',
      'RCTGeolocation',
      'RCTPushNotification',
      'RCTSettings',
      'RCTVibration',
      'RCTLinkingIOS',
      # 'RCTTest'
    ]
    pod 'Yoga', :path => './Other Sources/ReactNative/ReactCommon/yoga'
end

post_install do |installer_representation|
    # weak references are not supported in all Objective-C language modes so lets ensure to enable it
    # for some reason doing so also requires a deployment target which should be safe to explicitly add
    # here since this is post install and pod install should fail if the pod isn't supported by our platform flag
    installer_representation.pods_project.targets.each do |target|
        target.build_configurations.each do |config|
            config.build_settings['CLANG_ENABLE_OBJC_WEAK'] ||= 'YES'
            config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '8.0'
        end
    end
end
