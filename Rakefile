
require 'rake'

QC_EDITOR_PATH = '/Developer/Applications/Quartz Composer.app'

desc 'launch qc editor with composition'
task :run, [:composition_path] do |t, args|
  %x{ open -a '#{QC_EDITOR_PATH}' '#{args.composition_path}' }
end

# invoked by xcode runscript build phase
desc 'create archive of binary and docs for distribution'
task :create_archive, [:build_path, :version] do |t, args|
  # TODO - probably want to put this somewhere else
  dir_name = "CameraObscura_v#{args.version}"
  FileUtils.rm_rf(Dir.glob("#{dir_name}/*")) if File.exists? dir_name
  FileUtils.mkdir dir_name unless File.exists? dir_name

  FileUtils.cp_r args.build_path, dir_name
  FileUtils.cp %w(README.markdown TODO CHANGELOG Camera\ Capture.qtz), dir_name

  %x{ zip -r "#{dir_name}.zip" "#{dir_name}" }

  # TODO - open finder window to output location
end

# desc 'delete archive'
# task :clobber_archive
# end
