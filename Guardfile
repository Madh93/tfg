# A sample Guardfile
# More info at https://github.com/guard/guard#readme

## Uncomment and set this to only include directories you want to watch
# directories %w(app lib config test spec features) \
#  .select{|d| Dir.exists?(d) ? d : UI.warning("Directory #{d} does not exist")}

## Note: if you are using the `directories` clause above and you are not
## watching the project directory ('.'), then you will want to move
## the Guardfile to a watched dir and symlink it back, e.g.
#
#  $ mkdir config
#  $ mv Guardfile config/
#  $ ln -s config/Guardfile .
#
# and, you'll have to watch "config/Guardfile" instead of "Guardfile"

# Add files and commands to this file, like the example:
#   watch(%r{file/path}) { `command(s)` }
#
# guard :shell do
#   watch(/(.*).txt/) {|m| `tail #{m[0]}` }
# end
# guard :shell do
#   watch /.*/ do |m|
#     m[0] + " has changed."
#     m[1] + " has changed."
#   end
# end
guard :shell do
  watch /^([^\/]*)\.tex/ do |m|
    `echo #{m[0]} has changed at #{Time.now} >> log/guard.log`
    `make clean all > /dev/null 2>&1`
    if File.exists? "memtfg.ps"
      n "Built memtfg.pdf correctly", "Latex", :success
    else
      n "Failed to build memtfg.pdf", "Latex", :failed
    end
  end
end