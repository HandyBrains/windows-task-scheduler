# windows-task-scheduler

$User = "domain\Radhakrishnan.madhan"
$Time=New-ScheduledTaskTrigger -At 10.00AM -Daily -DaysInterval 1
$Action=New-ScheduledTaskAction -Execute PowerShell.exe -WorkingDirectory C:\utils\aws-pwsh\powershell-aws-main\ec2\ -Argument “C:\utils\aws-pwsh\powershell-aws-main\ec2\Instances_All_with_tags_V7_OneDrive.ps1"
Register-ScheduledTask -TaskName "ec2-inv-v1" -Trigger $Time -Action $Action -User $User -TaskPath \cad-aws -RunLevel Highest
Start-ScheduledTask -TaskName "ec2-inv-v1" -TaskPath \cad-aws\
