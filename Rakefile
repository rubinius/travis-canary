task :default do
  re = /^rubinius\s\d\.\d\.\d\.(([nmw]\d+)|(rc\d))\s\(#{ENV["RBX_RUBY_COMPAT"]}\s[0-9a-f]{8}\s\d{4}-\d{2}-\d{2}\sJI\)\s\[[^\]]+\]$/
  version = `rbx -v`.chomp
  unless re.match version
    STDERR.puts <<-EOM
Rubinius version output:
  #{version}
did not match:
  #{re.inspect}
    EOM
    exit 1
  else
    exit 0
  end
end
