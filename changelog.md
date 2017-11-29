# Version 1.7.1
- Added timestamping for password spraying
- Added timestamping for bad password count

# Version 1.7

## Big changes
- Introduced a credentials.yaml file so credentials are no longer passed via CLI
- Refined how all commands are initiated, instead of directly executing shell commands, each thread is now handled with Open3.popen2e
- New functions
  - run_cmd: Open3.popen2e deployer
  - load_creds: loads credentials from credentials.yaml
  - local_admin: List members who are local administrators on a remote host. (Requires a list of ip addresses with SMB open.)
  - remote_check: Uses socket with a 0.5 second connect_timeout to see if 445 is open on a remote host before sending commands
- Introduced credentials.yaml
- Introduced changelog.md

## Other changes
- Check if a file exists before opening it
- Fixed privileged user group enumeration, automato would error on "Enterprise Admins".
- Fixed attribute gathering and introduced "percentages"
- New functions
  - file_to_arr: refactoring how files are opened
  - output_file: refactoring how files are written
- Refactored the following methods:
  - ip_check, creds_check, enum_dom_users, enum_dom_groups, user_group_membership, enum_group_membership, priv_groups, grab_attr, bad_pw, all, domain_user_bf,
- Removed parallel processing with peach, the intention behind this is to use thread pools in a later realize

# TODO
- [TODO] is there a way to get individual directory objects (like bad password count) without pulling the entire user attributes?
- [TODO] FixedThreadPool for password spraying
- [TODO] FixedThreadPool for grabbing user attributes
- [TODO] NTLM hash support?