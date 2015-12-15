task :default do
  re = /^rubinius\s(\d+\.\d+(\.\d+)?)(\.c\d+)?\s\(#{ENV["RBX_RUBY_COMPAT"]}\s[0-9a-f]{8}\s\d{4}-\d{2}-\d{2}\s(JI)?\)\s\[[^\]]+\]$/

  version = `rbx -v`.chomp
  m = re.match version
  unless m
    STDERR.puts <<-EOM
Rubinius version output:
  #{version}
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

  exit 0
end
