# Cluster Update Checklist

Use this checklist when performing cluster updates to ensure all steps are completed correctly.

## Pre-Update Preparation

- [ ] Coordinate with team - Announce planned update in team channel
- [ ] Check for active sessions - Verify no one is currently using the cluster
- [ ] Review recent changes - Check GitLab activity log for new commits
- [ ] Backup current state - Document current image tags and versions

## Step 1: Repository & Registry Verification

- [ ] Check GitLab for updates in NGEN repository
  ```bash
  git fetch origin
  git log HEAD..origin/main --oneline
  ```
- [ ] Verify latest package in GitLab Package Registry
- [ ] Confirm target commit hash or tag

## Step 2: Pipeline Validation

- [ ] Navigate to GitLab CI/CD pipelines
- [ ] Verify latest pipeline is passing (green checkmark)
- [ ] Review test results and logs
- [ ] **If pipeline failing:** Use previous passing commit hash instead

## Step 3: Active Sessions Check

- [ ] Check for active user sessions
  ```bash
  docker ps -a
  ```
- [ ] Verify no running workflows on Parallel Works
- [ ] Confirm with team if any long-running jobs exist
- [ ] **If sessions active:** Wait or coordinate shutdown

## Step 4: Docker Image Management

- [ ] Pull latest image from registry
  ```bash
  docker pull [registry]/[image]:[tag]
  ```
- [ ] Verify image pulled successfully
  ```bash
  docker images | grep [image-name]
  ```
- [ ] Check disk space before cleanup
  ```bash
  df -h
  ```

## Step 5: Cleanup Operations

⚠️ **WARNING:** Never clean up if active sessions exist!

- [ ] Stop any old containers
  ```bash
  docker ps -a  # Review what's running
  docker stop [container-id]  # If needed
  ```
- [ ] Remove unused containers
  ```bash
  docker system prune -a --volumes
  ```
- [ ] Confirm cleanup completed
- [ ] Verify sufficient disk space remains

## Step 6: Tag Image as 'latest'

- [ ] Tag the pulled image as 'latest'
  ```bash
  docker tag [image]:[hash] [image]:latest
  ```
- [ ] Verify tag created
  ```bash
  docker images | grep latest
  ```
- [ ] Document the hash used for this tag

**Image hash used:** `________________________`

## Step 7: Build Singularity Container

⚠️ **CRITICAL:** Build ONE container at a time!

- [ ] **Verify no other builds running** (parallel builds crash cluster)
- [ ] Create TAR archive from Docker image
  ```bash
  docker save [image]:latest -o [image].tar
  ```
- [ ] Build Singularity SIF file
  ```bash
  singularity build [image].sif docker-archive://[image].tar
  ```
- [ ] Verify SIF file created successfully
  ```bash
  ls -lh [image].sif
  ```
- [ ] Test SIF file (optional but recommended)
  ```bash
  singularity exec [image].sif [test-command]
  ```

## Step 8: Update Downstream Repositories

Update the following repositories with new image references:

- [ ] **Account Manager**
  - Update image tag/hash
  - Commit and push changes
  - Verify pipeline passes
  
- [ ] **Forecast Manager**
  - Update image tag/hash
  - Commit and push changes
  - Verify pipeline passes
  
- [ ] **NWM Verf**
  - Update image tag/hash
  - Commit and push changes
  - Verify pipeline passes

**Notes on updates:**
```
Repo: ___________________  Hash: ___________________  Status: _______
Repo: ___________________  Hash: ___________________  Status: _______
Repo: ___________________  Hash: ___________________  Status: _______
```

## Step 9: Update UI and Server

- [ ] Navigate to UI/Server repository
- [ ] Run build script
  ```bash
  ./build_cluster.sh
  ```
- [ ] Monitor build output for errors
- [ ] Check build logs if any failures
- [ ] **If build fails:** Troubleshoot before proceeding

## Step 10: Build Verification

Check all builds completed successfully:

- [ ] NGEN core build - **Status:** ______
- [ ] Account Manager build - **Status:** ______
- [ ] Forecast Manager build - **Status:** ______
- [ ] NWM Verf build - **Status:** ______
- [ ] UI components build - **Status:** ______
- [ ] Server components build - **Status:** ______

**If any build failed:**
- [ ] Review error logs
- [ ] Check for configuration issues
- [ ] Verify all dependencies present
- [ ] Re-run failed build
- [ ] Document issue for team

## Step 11: Deploy to Parallel Works

- [ ] Log into Parallel Works platform
- [ ] Navigate to workflow section
- [ ] Select deployment workflow: `ngen_cerf_rtx_dev`
- [ ] Configure workflow parameters
- [ ] Start deployment
- [ ] Monitor deployment progress
- [ ] Check for any errors or warnings

## Post-Deployment Validation

- [ ] Verify cluster is accessible
- [ ] Test basic workflow execution
- [ ] Check all services responding
- [ ] Validate data paths correct
- [ ] Run smoke test (if available)
- [ ] **Deployment time:** ___________

## Documentation & Communication

- [ ] Update internal documentation with new versions
- [ ] Document any issues encountered
- [ ] Note any configuration changes made
- [ ] Announce completion to team
- [ ] Update this checklist if process changed

**Update completed by:** ___________________  **Date:** ___________

## Rollback Procedure (If Needed)

If critical issues discovered:

- [ ] Document the problem
- [ ] Revert to previous image tag
  ```bash
  docker tag [image]:[previous-hash] [image]:latest
  ```
- [ ] Rebuild Singularity containers with reverted image
- [ ] Notify team of rollback
- [ ] Create incident report

**Previous working hash:** `________________________`

## Troubleshooting Quick Reference

### Common Issues

**Pipeline Failing**
- Use previous passing commit hash
- Check test logs for specific failures
- Coordinate with development team

**Disk Space Issues**
- Run `df -h` to check space
- Perform more aggressive cleanup
- Remove old TAR archives
- Contact admin if critical

**Build Crashes**
- Ensure building ONE at a time
- Check system resources
- Verify no memory leaks
- Restart build service if needed

**Tag Not Found**
- Verify package registry access
- Check tag naming convention
- Confirm image pushed to registry

### Key Commands Reference

```bash
# Check disk space
df -h

# View Docker images
docker images

# View running containers
docker ps -a

# Pull specific image
docker pull [registry]/[image]:[tag]

# Tag image
docker tag [source] [target]

# Cleanup Docker
docker system prune -a --volumes

# Build Singularity
singularity build [output].sif docker-archive://[input].tar

# Git commands
git fetch origin
git log HEAD..origin/main
git stash save "WIP"
git stash pop
```

## Notes Section

Use this space for any additional notes or observations during the update:

```
___________________________________________________________________________
___________________________________________________________________________
___________________________________________________________________________
___________________________________________________________________________
___________________________________________________________________________
```

---

**Checklist Version:** 1.0  
**Last Updated:** November 2025  
**Next Review:** _____________
