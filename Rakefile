task :default do
  re = /^rubinius\s(\d+\.\d+(\.\d+)?)(\.c\d+)?\s\((\d+\.\d+\.\d+)\s[0-9a-f]{8}\s\d{4}-\d{2}-\d{2}\s\d+\.\d+(\.\d+)?(\sJI)?\)\s\[[^\]]+\]$/

  rbx_version = `rbx -v`.chomp
  m = re.match rbx_version
  unless m
    STDERR.puts <<-EOM
Rubinius version output:
  #{rbx_version}
did not match:
  #{re.inspect}
    EOM
    exit 1
  end

  version = ENV["RBX_VERSION"]
  unless m[1] == version
    STDERR.puts "Rubinius version #{m[1]} does not match expected #{version}"
    exit 1
  end

  compat_version = ENV["RBX_RUBY_COMPAT"]
  unless m[4] == compat_version
    STDERR.puts "Rubinius compatibility version #{m[4]} does not match #{compat_version}"
    exit 1
  end

  exit 0
end
