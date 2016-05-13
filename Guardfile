# A sample Guardfile
# More info at https://github.com/guard/guard#readme

# Config
Dir.mkdir('log') if !File.exists?('log')

# Recompile LaTeX
guard :shell do
  watch(%r{(.+)\.tex}) do |m|
    `echo #{m[0]} has changed at #{Time.now} >> log/guard.log`
    `make clean all > /dev/null 2>&1`
    if File.exists? "memtfg.ps"
      n "Built memtfg.pdf correctly", "Latex", :success
    else
      n "Failed to build memtfg.pdf", "Latex", :failed
    end
  end
end