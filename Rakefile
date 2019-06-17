# -*- coding: utf-8 -*-
$:.unshift("/Library/RubyMotion/lib")
$:.unshift("~/.rubymotion/rubymotion-templates")

# ===========================================================================================
# 1. Be sure to read `readme.md`.
# ===========================================================================================

require 'motion/project/template/ios'

begin
  require 'bundler'
  Bundler.require
rescue LoadError
end

# Uncomment the following line to add an icon generate capacity to your build
#task 'build:icons' => 'resources/app-icon.icon_asset'

Motion::Project::App.setup do |app|
  # Use `rake config' to see complete project settings.
  define_icon_defaults!(app)

  app.name = "Organizze"
  app.identifier = "com.organizze.2013"
  app.deployment_target = "11.2"
  app.short_version = "4.15.4"
  app.version = "4.15.4.0"

  app.archs['iPhoneOS'] = ['arm64']
  app.info_plist['UIRequiredDeviceCapabilities'] = ['arm64']

  app.device_family = [:iphone, :ipad]
  app.interface_orientations = [:portrait]
  app.info_plist['UIRequiresFullScreen'] = true
  app.info_plist['ITSAppUsesNonExemptEncryption'] = false

  app.info_plist['UIStatusBarStyle'] = 'UIStatusBarStyleLightContent'
  app.info_plist['UIViewControllerBasedStatusBarAppearance'] = false

  app.info_plist['UIBackgroundModes'] = ['remote-notification', 'fetch']


  app.pods do
    pod 'CorePlot', '2.2'
    pod 'MMMaterialDesignSpinner', '0.2.3'
    pod 'MGSwipeTableCell', '1.5.6'
    pod 'FBSDKCoreKit', '4.30.0'
    pod 'FBSDKLoginKit', '4.30.0'
    pod 'OneSignal', '2.3.5'
    pod 'AWSS3', '2.4.16'
    pod 'JTSImageViewController', git: 'git@github.com:organizze/JTSImageViewController.git'
    pod 'Harpy', '4.1.6'
    pod 'AHKNavigationController', '1.3'
    pod 'Shimmer', '1.0.2'
    pod 'Masonry', '1.1.0'
    pod 'GoogleSignIn', '4.4.0'
    pod 'UICollectionViewLeftAlignedLayout', '1.0.2'
    pod 'Firebase/Core'
    pod 'Firebase/RemoteConfig'
    pod 'Fabric'
    pod 'Crashlytics'
  end

  app.development do
    app.info_plist["debug_mode"] = true
    app.entitlements['aps-environment'] = 'development'
    app.codesign_certificate = MotionProvisioning.certificate(type: :development, platform: :ios)
    app.provisioning_profile = MotionProvisioning.profile(bundle_identifier: app.identifier, app_name: app.name, platform: :ios, type: :development)
  end

  app.release do
    app.info_plist["debug_mode"] = false
    app.entitlements['aps-environment'] = 'production'
    app.entitlements['beta-reports-active'] = true
    app.codesign_certificate = MotionProvisioning.certificate(type: :distribution, platform: :ios)
    app.provisioning_profile = MotionProvisioning.profile(bundle_identifier: app.identifier, app_name: app.name, platform: :ios, type: :distribution)
  end

  app.entitlements['com.apple.security.application-groups'] = ['group.com.organizze.2013']

  app.info_plist['FirebaseAppDelegateProxyEnabled'] = false
  app.entitlements['keychain-access-groups'] = [app.seed_id + "." + app.identifier]
end

def define_icon_defaults!(app)
  # This is required as of iOS 11.0 (you must use asset catalogs to
  # define icons or your app will be rejected. More information in
  # located in the readme.

  app.info_plist['CFBundleIcons'] = {
    'CFBundlePrimaryIcon' => {
      'CFBundleIconName' => 'AppIcon',
      'CFBundleIconFiles' => ['AppIcon60x60']
    }
  }

  app.info_plist['CFBundleIcons~ipad'] = {
    'CFBundlePrimaryIcon' => {
      'CFBundleIconName' => 'AppIcon',
      'CFBundleIconFiles' => ['AppIcon60x60', 'AppIcon76x76']
    }
  }
end
