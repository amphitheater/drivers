# drivers
function Get-DeviceInfo {
  $os_version = (Get-CimInstance Win32_OperatingSystem).Caption
  if ($os_version -match '.*Microsoft.*Windows.* (\d*) (.*)') {
    $os_num = $matches[1]
    $os_ed = $matches[2]
  }
  $os_architecture = (Get-CimInstance CIM_ComputerSystem).SystemType
  if ($os_architecture -match 'x64') {
    $os_architecture = 'x64'   
  } else {
    $os_architecture = 'x86'
  }
  $device_mfg = (Get-CimInstance CIM_ComputerSystem).Manufacturer
  $device_model = (Get-CimInstance CIM_ComputerSystem).Model
  $device_sn = (Get-CimInstance CIM_BIOSElement).SerialNumber
}
